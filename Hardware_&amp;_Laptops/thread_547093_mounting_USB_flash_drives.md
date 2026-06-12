---
title: "mounting USB flash drives"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by gaurav123 on 2007-09-09
hi,
i am an absolute novice to linux, so dont know much.  i have been trying to get images from my camera phone memory stick to the machine, but have run into problems.

1 ubuntu does not mount the disk. i have dbus and gnome volume manager, and have a fiesty fawn installed. but no auto recognition. 

2 i tried to go thru the terminal and editing the fstab. here is the code i typed AFTER making the directory /mnt/usb:

attempt 1:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /mnt/usb        auto    noauto,owner,kuzu       0       0

attempt 2:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /mnt/usb        ext3    noauto,owner,kuzu       0       2

the dmesg shows:
[ 1798.495075] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1799.573560] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5455.838934] cramfs: wrong magic
[ 5455.849981] VFS: Can't find ext3 filesystem on dev sda.
[ 5480.353605] cramfs: wrong magic
[ 5480.353823] attempt to access beyond end of device
[ 5480.353829] sda2: rw=0, want=4, limit=2
[ 5480.353837] EXT3-fs: unable to read superblock


i even tried changing the mount to /dev/sda2 but that does not work.

when i run lsusb, the output is:
root@gaurav1:~# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

and when i mount the ext drive, it says "already mounted", but the lsusb does not show that.

i tried using a different device - a USB flash drive - but that doesnt work too.

can someone help me with this? it would be really helpful if someone can give a dumbed down version of the steps, but if not, thats fine too...really looking forward for some help on this...!!
thanks

---

### Post by moore.bryan on 2007-09-09
*there are longer, more complex solutions, but you could just try installing ivman, run it, and see if it picks up your devices...*

---

