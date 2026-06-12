---
title: "Can't mount external Hard Drive, though can in XP"
date: 2010-02-23
forum: Hardware
---

### Post by sanchino on 2010-02-23
Hi everyone,

I've been checking the Forums and I can't find anything similar to my problem yet. I have 2 external drives that my UBUNTU 9.10 doesn't recognize, although I can see them perfectly in Win XP.

I was using them in Ubuntu until 2 weeks ago, when this problem started and I can't find a way to see/mount them again. GPARTED doesn't find any of them; and when aply **fdisk -l**, can't see them either (only my internal HD).

root@XXX-laptop:~# **dmesg | tail**
[  280.888096] usb 1-7: new high speed USB device using ehci_hcd and address 11
[  280.996321] hub 1-0:1.0: unable to enumerate USB device on port 7
[  386.580108] usb 1-4: new high speed USB device using ehci_hcd and address 12
[  386.692171] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 1225.305125] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1228.276117] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1231.244104] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1234.224129] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1234.336091] usb 1-7: new high speed USB device using ehci_hcd and address 17
[ 1234.448181] hub 1-0:1.0: unable to enumerate USB device on port 7

**PS:** I can read SD cards through USB; and I don't believe it's a USD cable problem 'cause I can see them in Win...

I've been struggling with this for over a week now... Any help will be appreciated!!

Thx

---

