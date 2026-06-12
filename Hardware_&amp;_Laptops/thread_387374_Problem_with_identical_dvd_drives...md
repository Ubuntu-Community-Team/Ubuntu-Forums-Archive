---
title: "Problem with identical dvd drives.."
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by yiannis_t on 2007-03-18
Hello to everybody!
I have a problem!  I have two identical dvd drives: NEC DVD+/-R/RW AD-7170A
In Computer - File browser only one is recognized..
Both work fine as long as i don't use them at the same time. If i put a dvd one the first one for example it runs fine as cdrom0.. if i remove it and put it to the second one it runs fine as cdrom0..
if i add two dvds on them it runs the dvd that has been insert first!

I  think there might have been some problem with the fstab file but i am not sure..PLEASE HELP!

---

### Post by yabbadabbadont on 2007-03-18
Please post the contents of your /etc/fstab file as well as the output of the following command:
```
dmesg | grep -i cdrom
```

---

### Post by yiannis_t on 2007-03-18
yiannis@ubuntu-desktop:~$ dmesg | grep -i cdrom
[17179672.812000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17179716.972000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17179951.864000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17179965.912000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17179981.940000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17179987.988000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17179990.000000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17184583.304000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17184589.324000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17184603.376000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17184683.656000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17184962.708000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17185464.624000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17185490.700000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17185492.704000] hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

---

### Post by tredegar on 2007-03-18
Have you checked the drive jumpers? If they are both on the same cable, one should be set as "Master", the other as "Slave".

And please post the contents of your /etc/fstab file...

---

### Post by yiannis_t on 2007-03-18
Yes the jumpers are set! The fstab file is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1e0ab13f-4b5c-45d4-acad-5d92218de796 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=8926269a-e803-4a4a-8964-ee3f8998db7e /home           ext3    defaults        0       2
# /dev/sda1
UUID=CCECB901ECB8E73C /mnt/drive_c    ntfs   defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=a611194b-eb5f-4d2f-a289-3da0153e8530 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto           0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto           0       0
/dev/           /media/floppy0  auto    rw,user,noauto            0       0
#/dev/sda1   /media/windows/  ntfs-3g  defaults,locale=el_GR.utf8   0       0

And it is set correct as i think..Don't you think?(ignore the last line..)

---

