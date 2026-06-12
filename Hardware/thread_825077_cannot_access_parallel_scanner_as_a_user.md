---
title: "cannot access parallel scanner as a user"
date: 2008-06-10
forum: Hardware
---

### Post by davidmohammed on 2008-06-10
Hi there,
  I have upgraded from gutsy to hardy - in the transition I have lost access to my parallel scanner.  I still have access as root.  Any ideas would be gratefully received?

These are some things I have checked.
My default user (daddy) is in the scanner group.
daddy@linux:~$ scanimage -L
device `v4l:/dev/video1' is a Noname DC10plus[0] virtual device
device `v4l:/dev/video0' is a Noname UNKNOWN/GENERIC virtual device
daddy@linux:~$ sudo scanimage -L
[sudo] password for daddy: 
device `v4l:/dev/video1' is a Noname DC10plus[0] virtual device
device `v4l:/dev/video0' is a Noname UNKNOWN/GENERIC virtual device
device `epson:0x378' is a Epson GT-5000 flatbed scanner
daddy@linux:~$ ls -l /dev/parport0
crw-rw---- 1 lp scanner 99, 0 2008-06-10 21:34 /dev/parport0

The other part of my setup is that I have a laserjet 4l also configure to use /dev/parport0 - however I dont think this is interfering since I have tried to delete the printer out of system-administration-printing.  Running xsane doesnt find the scanner.  Running sudo xsane does find the scanner device

---

