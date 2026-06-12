---
title: "Usb memory stick not mounting"
date: 2013-05-18
forum: Hardware
---

### Post by neigun on 2013-05-18
Hi Guys

First post for a while- good sign!

Anybody any idea how to enable automount for a usb memory stick?  This was working awhile back but on upgrade to Ubuntu Gnome 13.04 and a new rig it stopped working.  My external hard drive, keyboard and mouse are all working OK.  I've also tried lsusb to see if the system is detecting it which it appears to be doing.  Unfortunately I can't post the output as Ubuntu Gnome is playing silly buggers at the moment!

I'm using the 3.9 kernel and have the Gnome3 ppa installed.

Thanks in anticipation

Neil

System:

AMD FX-8320
M5A99X EVO R2.0
ATI 7750

---

### Post by ranger1021994 on 2013-05-18
Try editing fstab file located in /etc/fstab

---

### Post by neigun on 2013-05-18
Hi 

This is the contents of my fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=6157bb30-3832-40ce-b137-2be21eb4a945 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fab80716-a20a-490f-9279-ecca7e36d08a none            swap    sw              0       0

lsusb output is:
> Bus 003 Device 003: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 002: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 003: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 010 Device 002: ID 1058:1003 Western Digital Technologies, Inc. Elements 1000 GB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


What would I need to insert in the fstab file?

TTFN

---

### Post by ranger1021994 on 2013-05-18
Here :
This page describes the method
Tell me if it is working or not
It is for 12.10 but give it a shot
[http://www.liberiangeek.net/2012/12/how-to-auto-mount-external-usb-devices-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/12/how-to-auto-mount-external-usb-devices-in-ubuntu-12-10-quantal-quetzal/)

In quick it is:
OPen terminal : tpye ```
blkid
```
Locate your usb drive copy the UUID
Open fstab file
In the end add this
```
[FONT=consolas]UUID=XXXX-XXXX  /media/Backup vfat rw,user,suid,uid=1000,gid=1000,umask=000 0 0 [/FONT]


```
(You can choose your mount point instead of /media/Backup)

Now create a mount point directory:

```
sudo mkdir -p /media/Backup
```
(Or any other mount point of your choice)
And type this :
```
[FONT=Verdana]sudo chown -R username /media/Backup[/FONT]
```
[FONT=Verdana]where username is your username[/FONT]

---

### Post by neigun on 2013-05-21
Thanks Ranger when I get moment I'll give it a go.

---

### Post by neigun on 2013-09-23
Hi Ranger

Must have gone through an upgrade but it's working now.

Neil

---

