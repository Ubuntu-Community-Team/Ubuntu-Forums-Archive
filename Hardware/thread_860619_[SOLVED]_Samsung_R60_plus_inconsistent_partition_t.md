---
title: "[SOLVED] Samsung R60 plus inconsistent partition table"
date: 2008-07-15
forum: Hardware
---

### Post by Mago on 2008-07-15
I managed to install ubuntu with lilo (grub refused to install). Everything works except that now everytime i have to do a "sudo lilo", I need to give it the "IGNORE-TABLE" (-P ignore) command or it fails. I would't mind this if it weren't for the problem this created with dpkg and update-initramfs, which now refuses to configure.

I don't want to risk fixing the partition table (-P fix), that does not sound like a good thing to try.

Is there a way to add the lilo -P ignore to the dpkg --configure -a command? or at least to force dpkg ignore this step...




```
Warning: Device 0x0800: Inconsistent partition table, 2nd entry
  CHS address in PT:  653:0:1  -->  LBA (658224)
  LBA address in PT:  10490445  -->  CHS (10407:3:1)
Fatal: Either FIX-TABLE or IGNORE-TABLE must be specified
If not sure, first try IGNORE-TABLE (-P ignore)
```

---

### Post by beN..87 on 2008-07-15
you could try fixing it but you'll obviously need to back up first if you can get into your home folder somehow

your report says 2nd entry - sure thats ubuntu thts causing the problem?

also just make sure if you have Vista Longhorn loader installed that you set the bootable flag to OFF for your ubuntu partition or Windoze gets upset

my advice would be to write a new partition table, and just check that you are partitioning correctly - make sure you set the bootable flags correctly ect- theres plenty of MAN pages around

p.s see my posts for help with the r60 specifically - ive had no problems getting GRUB working on that notebook

---

### Post by Mago on 2008-07-15
As strange as it may seem, this R60 came with Win xp... it's from Germany (as in don't try to understand it)

The thing is that there isn't a "visible" problem. Win and Ubuntu both run fine. It's just that lilo doesn't configure unless I give it the -P ignore command... so update-initramfs does not work either and that's why I can't do a dpkg --configure -a... all of which leaves me with no apt-get and/or happiness.

sudo fdisk -l gives

```
Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x2fdc6822

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1         653     5245191   12  Compaq Diagnostics
/dev/sda2   *         654       10059    75547353+   7  HPFS/NTFS
/dev/sda3           10059       19458    75496448   83  Linux
```

sda2 ends on 10059 and sda3 starts also on 10059 and ends on 19458... that is what is probably causing the problem, but i didn't repartition or resize anything. All I did was to format sda3 to ext3. As you can see the bootable flag in sda3 is off.

---

### Post by Mago on 2008-07-15
Ok i've fixed it. The R60 has an option in bios for HDD mode (other / DOS)... it was in "other" for some reason... now with "DOS" it doesn't complain anymore. Maybe i could try installing grub now, but lilo is ok... it kinda grows on you.

---

