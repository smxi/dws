====================================================================
README for distrowatch.com stats tool: dws
====================================================================
FILE:    README.txt
VERSION: 1.2
DATE:    2018-10-22

====================================================================

git clone https://github.com/smxi/dws 

Install dws. Note that the -U (update) option means that only the
initial install is required:

wget -O dws https://github.com/smxi/dws/raw/master/dws

Shortcut download path for github (easier to remember and type):
wget -O dws smxi.org/dws

====================================================================
BASICS:

dws is a simple tool designed to check either a set of distro names 
or a top / bottom x number of distros from distrowatch.com.

You can use either -r or -d, but not both. Default is -r 10, -t 7.

--------------------------------------------------------------------
-d distro list:

The -d option is used like this:

dws -d arch,debian,ubuntu,fedora,opensuse

Note that no spaces or dashes are used in the distro names, and some,
like linux lite, are shortened to lite, e.g. PC-BSD is pcbsd, 
Ubunut Gnome is ubuntugnome, Tiny Core is tinycore, and so on. Only
ASCII characters can be used.

Known exceptions to distro naming:

Debian Edu: -d skolelinux
DragonFly: dragonflybsd
Emmabuntüs: -d emmabuntus
GoboLinux: -d gobo
HandyLinux: -d handy
Linux Lite: -d lite
MakuluLinux: -d makulu
MX Linux: -d mx
SparkyLinux: -d sparky
SUSE: -d sle
Ubuntu Christian: -d ubuntuce

-d overrides -r or configuration -r values.

--------------------------------------------------------------------
-r range:

-r with a positive integer between 1 and 99 shows the top x distros.

-r with a negative integer between -1 and -99 shows the bottom x
distros.

--------------------------------------------------------------------
-t time span:

The -t option sets the time interval. Accepts values 7 or 30 (days),
3, 6, or 12 months, and years from 2002 to current year. Output will
show for the requested interval. Default is 7 days. See below for 
examples.

--------------------------------------------------------------------
-U update:

This updates dws using github sources.

====================================================================
OUTPUT FORMAT:

From yesterday: + = rising; ~ = unchanged; - = falling. Does not show 
for year output.

Print Name: [ranking] (hits per day +~-) [working name, value for -d]

====================================================================
CHANGE DEFAULTS:

You can change the program defaults at top of program variable 
settings to what you want, just change the values of these top 
variables and $SELF_NAME 
will show by default what you want to see with no arguments/options:
DISTROS='debian,ubuntu,arch,antix' # show these distros by default
# or
RANGE=20 # show top 20 distros by default
TIME_SPAN='6' # show last 6 months

To make overrides permanent, put them into configuration file: 
/etc/dws.conf 

====================================================================
SAMPLES:

Here are a few samples to give you an idea of how the output looks.

--------------------------------------------------------------------
Default:

dws
Distrowatch.com 7 day rankings:
elementary:      1 (2509+)      [elementary]
Manjaro:         2 (2458+)      [manjaro]
MX Linux:        3 (1521+)      [mx]
Mint:            4 (1358+)      [mint]
Ubuntu:          5 (1278+)      [ubuntu]
KaOS:            6 (872+)       [kaos]
Debian:          7 (739+)       [debian]
MidnightBSD:     8 (658-)       [midnightbsd]
Lubuntu:         9 (624+)       [lubuntu]
Fedora:          10 (559+)      [fedora]

--------------------------------------------------------------------
Using negative Range, and Time:

dws -r -10 -t 12
Distrowatch.com 12 month rankings:

Neptune:         100 (122+)     [neptune]
Vector:          99 (126~)      [vector]
Black Lab:       98 (128~)      [blacklab]
Parabola:        97 (129-)      [parabola]
NuTyX:           96 (130-)      [nutyx]
Container:       95 (130~)      [container]
BunsenLabs:      94 (130~)      [bunsenlabs]
AUSTRUMI:        93 (130~)      [austrumi]
Elive:           92 (131~)      [elive]
SteamOS:         91 (132~)      [steamos]

--------------------------------------------------------------------
Using Positive Range, and Time:

dws -r 10 -t 12
Distrowatch.com 12 month rankings:
Manjaro:         1 (3356+)      [manjaro]
Mint:            2 (2574-)      [mint]
Ubuntu:          3 (1553-)      [ubuntu]
elementary:      4 (1494+)      [elementary]
Debian:          5 (1336-)      [debian]
MX Linux:        6 (1268+)      [mx]
Solus:           7 (1015-)      [solus]
Fedora:          8 (892~)       [fedora]
openSUSE:        9 (760~)       [opensuse]
Antergos:        10 (728-)      [antergos]

--------------------------------------------------------------------
Using Distro List, and Time

dws -d arch,gentoo,freebsd,sam,midnightbsd,fred,gus -t 30
Distrowatch.com 30 day rankings:
Arch:             15 (469-)     [arch]
Gentoo:           60 (185-)     [gentoo]
FreeBSD:          24 (368+)     [freebsd]
sam:              not ranked
MidnightBSD:      28 (329+)     [midnightbsd]
fred:             not ranked
gus:              not ranked

--------------------------------------------------------------------
Using Postive Range, and Year 

dws -r 6 -t 2015
Distrowatch.com 2015 year rankings:
Mint:            1 (3084)       [mint]
Debian:          2 (1810)       [debian]
Ubuntu:          3 (1617)       [ubuntu]
openSUSE:        4 (1341)       [opensuse]
Fedora:          5 (1148)       [fedora]
Mageia:          6 (1026)       [mageia]

