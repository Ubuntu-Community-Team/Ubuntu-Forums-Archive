---
title: "Hp Laserjet 2100 not printing properly"
date: 2014-03-07
forum: Hardware
---

### Post by PDA1 on 2014-03-07
I'm running Ubunt 10.04

My HP Laserjet 2100 used to print perfectly until 2 days ago when I installed another printer- an Hp officejet 8500. 

The 2100 is a parallel printer- not usb.

HPLIP was also installed.

Now, all the 2100 does is print 1 line of text on each page and doesn't stop printing the same stuff over and over again.

I deleted the officejet 8500 printer off of my system.

HP Device Manager doesn't do much good either.

Somehow I think it's related to the drivers but just don't know.

Can you please tell me how to revert back to "the good ol' days" when my 2100 worked?

---

### Post by phidia on 2014-03-07
Maybe [this]("https://wiki.ubuntu.com/DebuggingPrintingProblems") will help?

---

### Post by PDA1 on 2014-03-07
I'll give it a try tomorrow just to become familiar with the procedure.

I got the printer to work again. I tried the Gutenburg-Cups (pretty sure that's what it's called).

Thank you for the effort.

---

### Post by PDA1 on 2014-03-07
Here's the output of the help link you provided;

```
   Frank@Frank-desktop:~$  lsmod | grep lp  
 lp                      7028  0  
 parport                32635  3 ppdev,parport_pc,lp 
 drm_kms_helper         29329  1 i915 
 drm                   164468  5 i915,drm_kms_helper 
 Frank@Frank-desktop:~$ lsmod | grep ppdev  
 ppdev                   5259  0  
 parport                32635  3 ppdev,parport_pc,lp 

 Frank@Frank-desktop:~$  lsmod | grep parport_pc 
 parport_pc             26250  1  
 parport                32635  3 ppdev,parport_pc,lp 

 Frank@Frank-desktop:~$  dmesg | grep par  
 [    0.000000] Booting paravirtualized kernel on bare hardware 
 [    0.201223] pci 0000:00:1e.0: transparent bridge 
 [    0.217728] hpet0: 3 comparators, 64-bit 14.318180 MHz counter 
 [   13.925420] parport_pc 00:07: reported by Plug and Play ACPI 
 [   13.925478] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA] 
 [   14.015936] ppdev: user-space parallel port driver 
 [   14.017578] lp0: using parport0 (interrupt-driven). 

 Frank@Frank-desktop:~$  ls -l /dev/lp* /dev/parport*  
 crw-rw---- 1 root lp  6, 0 2014-03-07 21:00 /dev/lp0 
 crw-rw-r-- 1 root lp 99, 0 2014-03-07 21:00 /dev/parport0 

 Frank@Frank-desktop:~$ ls -l /proc/sys/dev/parport/parport*/autoprobe*   
 -r--r--r-- 1 root root 0 2014-03-07 21:13 /proc/sys/dev/parport/parport0/autoprobe 
 -r--r--r-- 1 root root 0 2014-03-07 21:13 /proc/sys/dev/parport/parport0/autoprobe0 
 -r--r--r-- 1 root root 0 2014-03-07 21:13 /proc/sys/dev/parport/parport0/autoprobe1 
 -r--r--r-- 1 root root 0 2014-03-07 21:13 /proc/sys/dev/parport/parport0/autoprobe2 
 -r--r--r-- 1 root root 0 2014-03-07 21:13 /proc/sys/dev/parport/parport0/autoprobe3 

 Frank@Frank-desktop:~$ sudo cat /proc/sys/dev/parport/parport*/autoprobe*  
 [sudo] password for Frank:  

 Frank@Frank-desktop:~$ lpinfo -v 
 network ipp 
 network http 
 network socket 
 network lpd 
 direct scsi 
 serial serial:/dev/ttyS0?baud=115200 
 direct parallel:/dev/lp0 
 network smb 
 network beh 
 direct hp 
 direct hpfax 

 Frank@Frank-desktop:~$ sudo -u 
 sudo: option requires an argument -- 'u' 
 usage: sudo -h | -K | -k | -L | -V 
 usage: sudo -v [-AknS] [-p prompt] 
 usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u 
             username|#uid] [-g groupname|#gid] [command] 
 usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u 
             username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>] 
 usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u 
             username|#uid] file ... 

 Frank@Frank-desktop:~$ sudo /usr/lib/cups/backend/parallel   
 direct parallel:/dev/lp0 "HP LaserJet 2100 Series" "HP LaserJet 2100 Series LPT #1" "MANUFACTURER:Hewlett-Packard;COMMAND SET:PJL,MLC,PCL,PCLXL;MODEL:HP LaserJet 2100 Series;CLASS:PRINTER;DESCRIPTION:Hewlett-Packard LaserJet 2100 Series" "" 

 Frank@Frank-desktop:~$ sudo /usr/lib/cups/backend/parallel 
 direct parallel:/dev/lp0 "HP LaserJet 2100 Series" "HP LaserJet 2100 Series LPT #1" "MANUFACTURER:Hewlett-Packard;COMMAND SET:PJL,MLC,PCL,PCLXL;MODEL:HP LaserJet 2100 Series;CLASS:PRINTER;DESCRIPTION:Hewlett-Packard LaserJet 2100 Series" "" 
 Frank@Frank-desktop:~$  


```

---

