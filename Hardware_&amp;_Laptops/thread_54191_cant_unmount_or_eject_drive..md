---
title: "cant unmount or eject drive."
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-08-03
havingg a little prob here
When i pout a cd in the drive it works fine. but when i want to take it out its anoyher story.

if i try to unmount by left clicking it say cannot unmount?? 
if i try to eject manually or laeft clicking , it says cannot eject. nothin is using the drive? sometimes it says you have to be loged in a sroot but not always,,,how do i do that?
I am currently "forcing" unmount in the termainl and in not great with it so i have to keep coming back here to paste the code..?
and thoughts.
thanx

---

### Post by amohanty on 2005-08-03
can you post your /etc/fstab file?

AM

---

### Post by floyd27 on 2005-08-03
here you go..


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by amohanty on 2005-08-03
Well everything looks good AFAIK. What does a normal:
>> sudo /media/cdrom0

return?

AM

---

