---
title: "/etc/fstab explanation required"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by sjunaidn on 2006-12-12
I have the following fstab file

> junaid@lightspeed:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# 
proc                    /proc   proc   defaults  0       0
/dev/mapper/Ubuntu-root / ext3  defaults,errors=remount-ro 0   1
/dev/sda5       /boot   ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none  swap    sw      0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto 0      0



I understand the bits where /dev/sda5 AND /dev/hda are being mounted to /boot and /media/cdrom mount points.

what i dont understand are the lines

/dev/mapper/Ubuntu-root / ext3  defaults,errors=remount-ro 0   1
/dev/mapper/Ubuntu-swap_1 none  swap    sw      0       0


I can understand that a device named /dev/mapper/Ubuntu-root AND /dev/mapper/Ubuntu-swap_1 is being mounted to mount points / and swap, but i dont have any such devices.

can any one please explain these entries to me?

thanks

---

### Post by Zelut on 2006-12-12
it looks to me like you've setup your partitions using LVM and those are your devices.

Those represent your hard drive and root partitions.. you're just using an LVM vs other setup is all.  Nothing looks out of the ordinary to me..

---

### Post by sjunaidn on 2006-12-12
yes thats right. I am using LVM.

I didnt know what it was but google has revealed that i made the right decision unintenationally :D 


now i need to learn how to use it.

thanks for the reply.

---

