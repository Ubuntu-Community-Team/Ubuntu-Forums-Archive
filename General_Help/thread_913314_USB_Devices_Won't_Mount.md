---
title: "USB Devices Won't Mount"
date: 2008-09-07
forum: General Help
---

### Post by dethredic on 2008-09-07
I have tried 2 mp3 players and a flash stick, but they don't mount. I get some error saying:


Cannot mount volume
Unable to mount the volume xxxxxxx

Details: mount: wrong fs type, bad option, bad superblock on / dev/sbd, missing codepage or helper program, or other error.

I have hardy. And my other Windows vista partition mounts fine.

---

### Post by dethredic on 2008-09-08
anyone?

---

### Post by triphazard on 2008-09-08
i don't suppose the device already has an (erroneous) entry in /etc/fstab does it?

what filesystem are the devices using?  do you notice anything odd in fdisk?

---

### Post by dethredic on 2008-09-08
Ok, one of the devices is a generic flash memory stick, another is an iPod, and the last is a P2 MP3 player (UMS firmware).

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=f6b4ac1a-a5cb-460d-acb3-a56f81a8ca86 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=addf90d5-1ef6-4783-a103-56ba0872b28d /home           ext3    relatime        0       2
# /dev/sda3
UUID=f466388d-d244-4d9d-be6a-d3ae8a020f67 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

That is with the iPod connected.

When I go to my computer, the device is there and its name is there. Also in the iPods case there is the iPod icon.

not sure what I am doing the fdisk.

---

### Post by triphazard on 2008-09-09
The fstab entry looks fine to me.

So in the left hand pane of Nautilus the devices show up?  That usually means they mounted ok.  Is it on clicking the devices from there that the error messages pop up or immediately when you plug in the device?

As for the fdisk, try whacking in "sudo fdisk -l" (lower case L) in a terminal window and it'll show you all the various disks and partitions on those disks.  From the size and filesystem you should be able to identify the mp3 player.  If we assume it's /dev/xyz1 try mounting it manually as below.

Create a mountpoint in /media "sudo mkdir /media/mp3" (or whatever name you like).

Mount the device with "sudo mount /dev/xyz1 /media/mp3".

That'll either work or, if not, hopefully give you a reason why not.  Sorry if you already know this stuff.

---

### Post by dethredic on 2008-09-09
> **triphazard said:**
> The fstab entry looks fine to me.

So in the left hand pane of Nautilus the devices show up?  That usually means they mounted ok.  Is it on clicking the devices from there that the error messages pop up or immediately when you plug in the device?
Yes the devices show up in the left pane. The error message comes up when I plug in the device and when I select it from that pane.

> **triphazard said:**
> 
As for the fdisk, try whacking in "sudo fdisk -l" (lower case L) in a terminal window and it'll show you all the various disks and partitions on those disks.  From the size and filesystem you should be able to identify the mp3 player.  If we assume it's /dev/xyz1 try mounting it manually as below.

Create a mountpoint in /media "sudo mkdir /media/mp3" (or whatever name you like).

Mount the device with "sudo mount /dev/xyz1 /media/mp3".

That'll either work or, if not, hopefully give you a reason why not.  Sorry if you already know this stuff.

> 
phil@Ubuntu:~$ sudo mkdir /media/shuffle
phil@Ubuntu:~$ sudo mount /dev/sdb /media/shuffle
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

phil@Ubuntu:~$ 


Darn, this is going in circles. I know this was working before, and tbh I am not sure when this started happening, cause I can't really recall trying to use any of these USB devices in the last month or so.

My only thought is that when I compiled a custom kernel I screwed up something with the USB recognition or something.

---

### Post by dethredic on 2008-09-11
anyone?

---

