---
title: "Ubuntu 14.04: Cant open storage area on USB player"
date: 2014-05-25
forum: Hardware
---

### Post by roadrash on 2014-05-25
Ever since using Ubuntu 14.04 I can no longer get into the storage area of my mp3 player which is a philips go-gear vibe.  When I plug it into a usb port its recognised and it puts the icon for it into unity panel.  when I select it it opens a window showing a drive icon called "Internal Storage".  If I open this it doesn't load list of contents.  Can someone help please.  Here are a few logs:

> lsusb
Bus 002 Device 004: ID 0471:207b Philips (or NXP) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Fou

> May 25 17:00:25 jon-Extensa-5220 kernel: [ 3740.412057] usb 2-1: new high-speed USB device number 6 using ehci-pci
May 25 17:00:25 jon-Extensa-5220 kernel: [ 3740.545241] usb 2-1: New USB device found, idVendor=0471, idProduct=207b
May 25 17:00:25 jon-Extensa-5220 kernel: [ 3740.545246] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
May 25 17:00:25 jon-Extensa-5220 kernel: [ 3740.545249] usb 2-1: Product: GoGear Vibe
May 25 17:00:25 jon-Extensa-5220 kernel: [ 3740.545252] usb 2-1: Manufacturer: Philips
May 25 17:00:25 jon-Extensa-5220 kernel: [ 3740.545254] usb 2-1: SerialNumber: 310F0000C979DAB40002DA734DABDAB4
May 25 17:00:25 jon-Extensa-5220 kernel: [ 3740.546775] usb-storage 2-1:1.0: USB Mass Storage device detected
May 25 17:00:25 jon-Extensa-5220 kernel: [ 3740.546926] scsi8 : usb-storage 2-1:1.0
May 25 17:00:25 jon-Extensa-5220 colord: Device added: sysfs-Philips-GoGear_Vibe
May 25 17:00:25 jon-Extensa-5220 colord: Device added: sysfs-(null)


> NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 109.8G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0     2G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  



---

### Post by Jonor on 2014-05-26
Have you tried accessing it as root user ?

```
sudo nautilus
```

---

