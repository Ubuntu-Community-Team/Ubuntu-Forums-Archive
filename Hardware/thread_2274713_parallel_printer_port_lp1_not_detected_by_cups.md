---
title: "parallel printer port lp1 not detected by cups"
date: 2015-04-21
forum: Hardware
---

### Post by rmisk on 2015-04-21
Whenever I try to print using usb-parallel or parallel (lp1 is where the HP LaserJet 2100 appears to be now) I spend hours trying to get it to work.  This time after several hours CUPS still doesn't find it.  I have tried everything I have found with google.  I hate Windows but at least it always prints!  

Does anyone know of a reliable and robust setup procedure that will setup printers in xubuntu that will work every time (well say 99/100 times) I need it instead of (1/500 times)?

Here is some info that may or may not be of use:

~$ sudo /usr/lib/cups/backend/parallel
direct parallel:/dev/lp0 "unknown" "LPT #1" "" ""
direct parallel:/dev/lp1 "HP LaserJet 2100 Series" "HP LaserJet 2100 Series LPT #2" "MANUFACTURER:Hewlett-Packard;COMMAND SET:PJL,MLC,PCL,PCLXL,POSTSCRIPT;MODEL:HP LaserJet 2100 Series;CLASS:PRINTER;DESCRIPTION:Hewlett-Packard LaserJet 2100 Series" ""
direct parallel:/dev/lp2 "unknown" "LPT #3" "" ""
~$ lpinfo -v
file cups-pdf:/
network https
network socket
network ipp
network http
network ipps
serial serial:/dev/ttyS0?baud=115200
network ipp14
network lpd
network smb

Note: no direct parallel port  found.

~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
ppdev


Printers should just work!

Copying pdf to memory stick and printing at Staples is not something that sells Linux!

---

### Post by Vladlenin5000 on 2015-04-22
Do you have HPLIP installed? If not you should...

---

