---
title: "Internal Hard Drives unmounted"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by alvarez1900 on 2007-11-04
I am fairly new to Ubuntu and have had some luck learning it. I have been converting people left and right to ubuntu as well because the system is so amazing on my laptop everyone wants the effects and stability I have on my system. I am a guitar teacher and incorporate my laptop to our lessons and learning a lot.

 However out of nowhere my drives vanished. I have 13 gigs dedicated to Gutsy and then 93 gig to windows. On my 2nd harddrive I have the full drive devoted to music etc and its NTFS.

 Both the NTFS drives have vanished and when running fdisk -l they show there but are unmounted. 1st off how do I get them remounted and 2nd off why did this happen? I never had this problem under feisty.

---

### Post by markusf21 on 2007-11-04
If you did a hard shutdown from windows and then boot to ubuntu the windows drives won't mount

---

### Post by alvarez1900 on 2007-11-04
> **markusf21 said:**
> If you did a hard shutdown from windows and then boot to ubuntu the windows drives won't mount

 I have rebooted both OS'es for going on 2 days now and still they won't mount.

---

### Post by coolrohan on 2007-12-06
I have a similar problem with my laptop, where the drives suddenly get unmounted. i also have a NTFS drive, and after a while, it stops showing the contents of the drives. The internal drives ie HDD becomes unmounted, in such a way, that i cannot access any data in the drives. when i use sudo fdisk -l, it shows the drives mounted, but i cannot access them.

---

### Post by Yellow Pasque on 2007-12-06
Try:
```
sudo mount -a
```

Also, please post your /etc/fstab file.

---

### Post by coolrohan on 2007-12-07
hey, i tried searching for that fstab file in the etc folder, but could not find it anywhere. as of now, the drives are mounted, but suddenly, when am working, the drives dissapear. and i cannot access the information. the next time this happens, i will use the code you gave
 and this is the fstab information:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=475d8252-42b2-451c-ae34-0bf5609a3d06 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8C2C80FA2C80E116 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=38F05C3CF05BFE96 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=5ff76594-d6ac-4b11-bad4-b855416c6d61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by zirbs on 2007-12-08
> **markusf21 said:**
> If you did a hard shutdown from windows and then boot to ubuntu the windows drives won't mount

I'm having this issue too. I have two NTFS windows partitions, one for the XP install, and one for storage, and my Ubuntu partition and swap partition.  Initially, both NTFS partitions would show up as mounted and I could access all data in them.  But now I cannot access the XP install partition, only the NTFS storage partition.  Is there a way I can get the XP partition to mount again?

edit: here's my fstab info, too.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6ac28473-f84b-4f54-ac43-665ccb7e2e40 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B4C4A6DAC4A69E5C /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=01C826F218331080 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=4b680b56-5751-4bfe-aae0-20bb4fb7583b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by dev3 on 2007-12-12
Anybody has any ideas about this??

---

