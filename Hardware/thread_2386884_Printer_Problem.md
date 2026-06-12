---
title: "Printer Problem"
date: 2018-03-11
forum: Hardware
---

### Post by oeblio2 on 2018-03-11
I have a LaserJet 1100 that was connected to UbuntuStudio 16.04. It worked great for many years. The parallel cable went bad and a wireless printer was installed and worked ok. The wireless printer died so I reinstalled the LaserJet 1100. Installation went ok. The printer will print but it takes about 45 minutes to complete a single page job. 

I ran a diagnostic I got from linux.org. Here are the results:

```
michael@michael-P5QL-PRO:~$ lsmod | grep lp
lpc_ich                24576  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
drm_kms_helper        155648  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  9 ttm,drm_kms_helper,nouveau
michael@michael-P5QL-PRO:~$ lsmod | grep ppdev
ppdev                  20480  0
parport                49152  3 lp,ppdev,parport_pc
michael@michael-P5QL-PRO:~$ lsmod | grep parport_pc
parport_pc             32768  1
parport                49152  3 lp,ppdev,parport_pc
michael@michael-P5QL-PRO:~$ dmesg | grep par
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] vt handoff: transparent VT on vt#7
[    0.118824] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.837444] Asymmetric key parser 'x509' registered
[   13.870328] ppdev: user-space parallel port driver
[   13.929127] PCI parallel port detected: 9710:9805, I/O at 0xe880(0xe800), IRQ 18
[   13.929177] parport0: PC-style at 0xe880 (0xe800), irq 18, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[   13.943083] parport0: Printer, Hewlett-Packard HP LaserJet 1100
[   13.943225] lp0: using parport0 (interrupt-driven).
[   20.217660] audit: type=1400 audit(1520559273.808:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="system_tor" pid=700 comm="apparmor_parser"
[   20.267150] audit: type=1400 audit(1520559273.858:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=699 comm="apparmor_parser"
[   20.267164] audit: type=1400 audit(1520559273.858:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=699 comm="apparmor_parser"
[   20.267171] audit: type=1400 audit(1520559273.858:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=699 comm="apparmor_parser"
[   20.267180] audit: type=1400 audit(1520559273.858:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=699 comm="apparmor_parser"
[   20.295362] audit: type=1400 audit(1520559273.886:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=698 comm="apparmor_parser"
[   20.295377] audit: type=1400 audit(1520559273.886:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=698 comm="apparmor_parser"
[   20.341121] audit: type=1400 audit(1520559273.932:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=719 comm="apparmor_parser"
[   20.374937] audit: type=1400 audit(1520559273.965:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=718 comm="apparmor_parser"
[   20.374952] audit: type=1400 audit(1520559273.965:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=718 comm="apparmor_parser"
michael@michael-P5QL-PRO:~$ ls -l /dev/lp* /dev/parport*
crw-rw---- 1 root lp  6, 0 Mar  8 17:34 /dev/lp0
crw-rw-r-- 1 root lp 99, 0 Mar  8 17:34 /dev/parport0
michael@michael-P5QL-PRO:~$ ls -l /proc/sys/dev/parport/parport*/autoprobe* 
-r--r--r-- 1 root root 0 Mar  9 08:21 /proc/sys/dev/parport/parport0/autoprobe
-r--r--r-- 1 root root 0 Mar  9 08:21 /proc/sys/dev/parport/parport0/autoprobe0
-r--r--r-- 1 root root 0 Mar  9 08:21 /proc/sys/dev/parport/parport0/autoprobe1
-r--r--r-- 1 root root 0 Mar  9 08:21 /proc/sys/dev/parport/parport0/autoprobe2
-r--r--r-- 1 root root 0 Mar  9 08:21 /proc/sys/dev/parport/parport0/autoprobe3
michael@michael-P5QL-PRO:~$ sudo cat /proc/sys/dev/parport/parport*/autoprobe*
[sudo] password for michael: 
CLASS:PRINTER;
MODEL:HP LaserJet 1100;
MANUFACTURER:Hewlett-Packard;
DESCRIPTION:HP LaserJet 1100 Printer;
COMMAND SET:MLC,PCL,PJL;
michael@michael-P5QL-PRO:~$ lpinfo -v
direct parallel:/dev/lp0
serial serial:/dev/ttyS0?baud=115200
network beh
network https
network http
network ipp
network ipps
direct hp:/par/HP_LaserJet_1100?device=/dev/parport0
network lpd
network ipp14
network socket
direct hpfax
michael@michael-P5QL-PRO:~$ /usr/lib/cups/backend/parallel
michael@michael-P5QL-PRO:~$ sudo /usr/lib/cups/backend/parallel
direct parallel:/dev/lp0 "HP LaserJet 1100" "HP LaserJet 1100 LPT #1" "MFG:Hewlett-Packard;MDL:HP LaserJet 1100;DES:HP LaserJet 1100 Printer;CMD:MLC,PCL,PJL;CLS:PRINTER;REV:1.1;IO PREFS:ECP18;" ""

```
I have tried hp, foomatic and gugenprint drivers. They all seem to work but printing takes 45 minutes for a single page. Any ideas?

Michael Alexander

---

### Post by HermanAB on 2018-03-12
Hmm, 45 minutes is a wee little bit excessive...

The problem with a GUI system is that you don't get any error messages.  To see what is up, you need the command line.

Make a short text file:
```
$ echo "Hello world!" > file.txt
```

Send it to the default printer:
```
$ lpr -P localhost file.txt
```

---

### Post by slickymaster on 2018-03-12
*Thread moved to **Hardware**.*

---

### Post by oeblio2 on 2018-03-12
Thanks for the quick  reply.

michael@michael-P5QL-PRO:~$ echo "Hello World" > file.txt
michael@michael-P5QL-PRO:~$ lpr -P localhost file.txt
lpr: The printer or class does not exist.

---

