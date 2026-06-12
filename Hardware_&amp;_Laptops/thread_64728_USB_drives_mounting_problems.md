---
title: "USB drives mounting problems"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by P0S3R on 2005-09-11
Hello all

Well.. just can't seem to mount usb external drives, i've an ipod mini and a Maxtor OneTouch drive.

When i tried to mount the maxtor i got this:

 /dev/scsi/host1/bus0/target0/lun0: p1 p2
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete
FAT: bogus logical sector size 2
VFS: Can't find a valid FAT filesystem on dev sda.
usb 1-1: USB disconnect, address 2

when i tried to moun the ipod got this:

usb 1-1: new full speed USB device using uhci_hcd and address 2
usb 1-1: not running at top speed; connect to a high speed hub
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 12000556 512-byte hdwr sectors (6144 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
SCSI device sda: 12000556 512-byte hdwr sectors (6144 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through

In the device manager i can see the ipod.. looks everything ok.. but can't access it, the maxtor does not appear. Got this problems after using ubuntu update manager and installed all that stuff, only things i've installed were in the starter guide.

Does anyone have a clue of whats happening?

Thanks

---

### Post by mlomker on 2005-09-11
Are you saying that the iPod shows up on your desktop as an icon but then you can't see anything on it?  I don't have one, myself, but if someone else can help they'll need more details.

The error for the Maxtor more or less states what it thinks the problem is--it can't find a filesystem on the device.  Did you just buy it or have you used it on another machine before?  It'll have to be formatted before you can use it.  You can format it on a Windows machine or look up the commands for linux (fdisk and mke2fs).

---

### Post by P0S3R on 2005-09-11
The ipod icon does not appear in my desktop, in my computer it creates usb, usb0 and usbdisk. The maxtor drive if it was left running when restarting/closing was on this OS ubuntu, only thing i've done was unplugging it without unmount on this system.. if that screwed all my usb mounting.. what can i do?

If anyone needs more info please just let me know and how to give them.

Thanks mlomker for the reply but formatting the maxtor it's out of question.

PS: Me nb in this OS (lol who'd say? :P)

---

### Post by mlomker on 2005-09-12
What file system is on the Maxtor?  Was it formatted on a PC?

Not all USB devices can be mounted as a disk (you might have to use a software program to access them).  What model of iPod do you have?  You should check to see if it is possible to mount one as a disk.  I don't have an iPod, so I do not know.

Plug them in one at a time and type this in a terminal prompt:

[b]
sudo fdisk -l
sudo cat /proc/scsi/scsi
[/b]

If linux sees them in both commands then you can add an entry to the /etc/fstab file and use the **mount** command to manually mount them.

---

### Post by P0S3R on 2005-09-12
Both usb devices mounted with no problem in ubuntu OS, on other installs, and in this one too, the problem i think was when i unplugged the maxtor usb cable without unmount the drive, after that it screwed up everything related to external storage disks via usb.

I've and ipod mini 6gb, worked perfectly in this same OS and so the Maxtor One Touch 160gb.

If i can't find a solution i think i'll have to reinstall the whole OS again lol.

=)

---

### Post by P0S3R on 2005-09-12
This is the msg that i get when i try to enter the usb0 in "Computer".

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If anyone have any ideas pls share

Thanks

---

### Post by Nick-xx on 2006-12-04
Oh Man don't be stupid don't install it again! This problem is happening a lot of people :) , even with other distro and in other forums(and even in me :-| ), i spend lot of time to try to figure out why it can't mount in vfat even my usb flash drive is fat16. Then i remember to see the /etc/filesystem (or if you don't have try /proc/filesystem then open that file with sudo and see if there is a vfat listed here, if don't have add it to the final line without the "no device" like this ex:

> no device usbfs
no device nfs
                 ext3
              **vfat**
When i mount it again with -t vfat it has mounted :mrgreen: (i think its a bug from the xubuntu edgy, i don't know if ubuntu or kubuntu has the same problem.) I hope this post has helped someone .

---

### Post by JayRoe on 2007-01-03
Hi, I'm a complete newbie when it comes to ubuntu, so could someone tell me how I save the changes I make to /proc/filesystems. I can edit and add vfat with sudo nano /proc/filesystems, but when I save the changes with ctrl o, nothing is saved the next time I open the file. Thanks in advance.

---

