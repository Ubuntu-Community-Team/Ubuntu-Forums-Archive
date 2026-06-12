---
title: "Installing HP OfficeJet 5610 and sharing it"
date: 2009-10-19
forum: Hardware
---

### Post by jon80 on 2009-10-19
I would like to install, preferably the latest driver for HP Officejet 5610 and share it (e.g. using CUPS).

However, I could not find any relevant options in the UI, and, I have to resort to the command line; is this so?

It seems that I have to update my driver to version 3.9.8, presumably by uninstalling and re-installing it again.  Is it possible to update?  How?

There are instructions on applying the patch ([http://hplipopensource.com/node/187](http://hplipopensource.com/node/187)), but I'm not sure whether I have to do this with the file I downloaded (**hplip-3.9.8.run**)

administrator@elsueno:~/Desktop$ vi hplip-3.9.8.run
...
administrator@elsueno:~/Desktop$ ./hplip-3.9.8.run
bash: ./hplip-3.9.8.run: Permission denied
administrator@elsueno:~/Desktop$ sudo .hplip-3.9.8.run
...
administrator@elsueno:~/Desktop$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                    Version                                 Description
+++-=======================================-=======================================-====================
ii  hplip                                   3.9.2-3ubuntu4                          HP Linux Printing an
administrator@elsueno:~/Desktop$ ls
Home.desktop  hplip-3.9.8.run  trash.desktop
administrator@elsueno:~/Desktop$ mkdir hplip
administrator@elsueno:~/Desktop$ mv *.run hplip
administrator@elsueno:~/Desktop$ cd hplip
administrator@elsueno:~/Desktop/hplip$ ls
hplip-3.9.8.run
administrator@elsueno:~/Desktop/hplip$ ls
hplip-3.9.8.run
administrator@elsueno:~/Desktop/hplip$ ./hplip-3.9.8.run
bash: ./hplip-3.9.8.run: Permission denied
administrator@elsueno:~/Desktop/hplip$

:confused:

Related Links:
1. [http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

NOTE
hplip-3.9.8.run is a script file..
#!/bin/sh
# This script was generated using Makeself 2.1.5

CRCsum="3873069307"
MD5="d91761d513cae77cf69f4f71b7c6ec95"
TMPROOT=${TMPDIR:=/tmp}

label="HPLIP 3.9.8 Self Extracting Archive"
script="./hplip-install"
scriptargs=""
targetdir="hplip-3.9.8"
filesizes="15715138"
keep=y

print_cmd_arg=""
if type printf > /dev/null; then
    print_cmd="printf"
elif test -x /usr/ucb/echo; then
    print_cmd="/usr/ucb/echo"
else
    print_cmd="echo"
fi

unset CDPATH

MS_Printf()
{
    $print_cmd $print_cmd_arg "$1"
}

MS_Progress()
{
    while read a; do
        MS_Printf .
    done
}

MS_diskspace()
{
        (
        if test -d /usr/xpg4/bin; then
                PATH=/usr/xpg4/bin:$PATH
        fi
...

---

