---
title: "Cannot Mount Volume"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by vbrew021 on 2007-11-04
I am new to Ubuntu and I am attempting to access my usb external hard drive, however, I get the unable to mount volume error when I connect it.  Can anyone help me with mounting the device?  I'm not sure if this matters but I have a Speedano 3 BMC 3.5 external hard drive with an NTFS partition, since it was originally used with Windows XP.  If anyone can help it would be greatly appreciated.

---

### Post by meroUno on 2007-11-05
I'm having the same problem somewhat.  Installation of Ubuntu picked up and mounted the hard drive, but then I unmounted it.  I wanted to mount it under my home folder but now I cannot mount anywhere.  Linux Lover since yesterday!

---

### Post by HareBall on 2007-11-05
I also have this problem. I had it mounted the other day and now it is unmounted and will not let me mount it.

"EDIT" I found another place and found that you can mount a drive by opening a terminal and typing```
sudo mount /dev/sdb1
```
sdb1 needs to be changed to the drive "name" you are wanting to mount.

---

### Post by chrisplod on 2007-11-05
Is there anyway to set it to mount automatically everytime the system starts?

---

### Post by vanadium on 2007-11-05
An USB external hard drive by default mounts automatically with rights for the user (this can be disabled in System - Preferences - Removable drives and media). If it should, but it doesn't, then it might be due to inconsistencies in the file system. At that point, the partition must first be checked and repaired before it will automount again.

To avoid file system damage, always make sure to properly unplug an usb drive: first "inmount"or "eject" it right-clicking on its icon or using the terminal (eject <devicename>), then remove it physically.

---

### Post by petteriIII on 2007-11-05
> **vanadium said:**
> An USB external hard drive by default mounts automatically with rights for the user ....

If only it were the rights for the user. My belief is that it mounts with those rights gparted has given; and in my machine at least it is the rights of root. And why many are complaining that they a allowed to write to USB-HD only when being root ? And by the way if you change those rights by hand you may always write to USB-hd. 

It must be that this depends from something strange, and is different for some PC:s.

---

### Post by vbrew021 on 2007-11-05
So far non of these things has helped.

---

### Post by vanadium on 2007-11-06
Did you check the volume for errors?

---

### Post by vbrew021 on 2007-11-07
Yes I have checked the volume for errors and there are none.

---

### Post by xtigma on 2007-11-07
Hello there. 
I am a Ubuntu new user.
I found out that if you edit the file /etc/fstab you can add automount drives
add this line...

/dev/hda1 /mnt/hda1 ext3 auto,user,exec 0 0

let me explain as I understand

dev/hda1 is like HD=Hard Disk   A=(primary) 1=(partition#1)
dev/ is a folder where the devices you use are listed like sound card a stuff.

mnt/ is where mounted devices are listed

the next part EXT3 is the file system of the Disk.
AUTO.USER.EXEC gives the instruction to automount device.
(zero) (zero) indicates is the first device and first partition.
I mean 0 is the first, 1 is second, 2 is third...

but there is a con...

I don't know how to edit my fstab on Ubuntu cause it looks weird to me. like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c5649b37-cf18-438d-9911-5abbe9c22cab /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=23faf45a-2170-44ae-afd5-42c3bf0429d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

ok. this shows an exact mounting point of my first partition:

# /dev/sda1
UUID=c5649b37-cf18-438d-9911-5abbe9c22cab /               ext3    defaults,errors=remount-ro 0       1

where my disk label is commented with # and the drive has an S and not appears like HDA, that's because new linux distros changes the letter depending it is a SATA or ATA Drive. <please correct me if I am wrong>

also it shows:

# /etc/fstab: static file system information.

here fstab says us that this drives dont move, are static. here is where we put our internal drives. 
but if you have an external drive. Pluggable devices are handled by uDev, they are not in fstab...

for example I added a Hard Disk it is internal: just made this


/dev/sdb1 /mnt/sdb1 fat32 auto user,auto,exec 0	0

Hope this can help

please someone that knows more correctme if I am Wrong, but this is what I have learned in 4 hours.

---

### Post by vanadium on 2007-11-08
xtigma, your summary looks pretty accurate to me. Indeed, you have permanent drives that are mounted through /etc/fstab. However, a hotpluggable USB drive should mount automatically, and if it doesn't, then there is a problem with the volume or the hardware, or perhaps with the latest kernel. It is always a good idea to post the full error message when reporting a problem: this leaves less to be guessed.

---

