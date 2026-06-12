---
title: "Ubuntu Grub and Windows"
date: 2008-11-07
forum: General Help
---

### Post by TransitMan on 2008-11-07
I recently had to reinstall WinXP.
I installed this on a drive that according to fstab is sdc1.
Further, when I installed XP, in the BIOS I disabled the other 3 SATA drives.
Upon completeing the installation, I re-initialized the other SATA drive and attempted a restore of GRUB as viewed throughout this forum and then some. However, all the written tutorials reference hd0, hd1, hd2 and so on. These tutorials assume Windows is installed on the first drive.
I have used Super Grub without success. It does not see the Windows installation.
I know it is a matter of editing the /menu.lst for grub, but I need to know the proper hd? for sdc1. Below is the current entry in the /menu.lst
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
Anyone with a suggestion, short of reinatallation of 8.04.1?

---

### Post by tiberiup on 2008-11-07
for sdc1 in grub : (hd2,0)
a=0,b=1,c=2...
1=0,2=1,3=2...

---

### Post by caljohnsmith on 2008-11-07
So are you booting directly into Windows right now, or do you get a Grub menu if you boot a particular drive? 

From your Live CD, how about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by TransitMan on 2008-11-07
BTW, I am booting into Ubuntu normally via grub.

From sudo fdisk -lu
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b230b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      385559      192748+  83  Linux
/dev/sda2          385560    10153079     4883760   83  Linux
/dev/sda3        10153080    14056874     1951897+  82  Linux swap / Solaris
/dev/sda4        14056875   156248189    71095657+   5  Extended
/dev/sda5        14056938    33591914     9767488+  83  Linux
/dev/sda6        33591978    41399504     3903763+  83  Linux
/dev/sda7        41399568    60934544     9767488+  83  Linux
/dev/sda8        60934608    66798269     2931831   83  Linux
/dev/sda9        66798333   156248189    44724928+   b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34783ca1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c7399

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    30716279    15358108+   7  HPFS/NTFS
/dev/sdc2        30716280   312576704   140930212+   7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb215b215

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   390716864   195358401    7  HPFS/NTFS

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8be2f02b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   625137344   312568641    7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfd37cde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3d8e295

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   156296384    78148161    7  HPFS/NTFS
/dev/sdg2       156296385   312576704    78140160    7  HPFS/NTFS
```

For the command sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
0000000 0000                                   
0000002

```

The other command sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system" results are
```
Missing operating system
```

For tiberiup - I have tried the (hd2,0) with no success.

---

### Post by caljohnsmith on 2008-11-07
So you are able to boot into Ubuntu OK? Because it doesn't look like you have Grub installed to the MBR (Master Boot Record) of sda. But go ahead and first pull up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom, replace your existing Windows entry with:
```

title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title	   Windows XP (hd4)
root       (hd4,0)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1

title	   Windows XP (hd5)
root       (hd5,0)
map        (hd0) (hd5)
map        (hd5) (hd0)
chainloader +1

title	   Windows XP (hd6)
root       (hd6,0)
map        (hd0) (hd6)
map        (hd6) (hd0)
chainloader +1
```
In case you are wondering, the reason we need to try six different entries for Windows is that I have no way of knowing which drive Windows is on in your BIOS boot order, so the easiest way is to just try all six possible combos. Give that a shot, and if for some reason none of them work, let me know exactly what happens when you try each one on start up. Otherwise let me know how it goes.

---

### Post by TransitMan on 2008-11-07
Results of the combos given above resulted in the following - 
HD1, HD2, HD3, HD4 - Error 11, Unrecognized device string
HD5, HD6 - Error 21, Selected Disk does not exist.

My "grub" is located in a separate partition /boot on /dev/sda

In the BIOS, Windows XP is the first partition on SATA2, which is where I am typing from right now after disabling SATA0, SATA1, and SATA3.
After posting this, I am returning to Ubuntu.

---

### Post by caljohnsmith on 2008-11-07
> **TransitMan said:**
> Results of the combos given above resulted in the following - 
[COLOR="Blue"]HD1, HD2, HD3, HD4 - Error 11, Unrecognized device string[/COLOR]
HD5, HD6 - Error 21, Selected Disk does not exist.

My "grub" is located in a separate partition /boot on /dev/sda

In the BIOS, Windows XP is the first partition on SATA2, which is where I am typing from right now after disabling SATA0, SATA1, and SATA3.
After posting this, I am returning to Ubuntu.
Did you manually type in those entries I gave, or copy/paste and them? An error 11 usually means you have a typo in the menu.lst entry. Did you use the letter O instead of the number 0 for example? Try copying/pasting those exact entries I gave and let me know the results.

---

### Post by TransitMan on 2008-11-07
I typed them in, using number 0 and not letter O.
Not to sure why, but I went back and copied/pasted and tried again starting with 
```
title	   Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
which resulted in BOOTMGR is Missing, Press Ctrl+Alt+Del to restart.

Then went and copied/pasted
```
title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
which resulted in booting into Windows XP.
I now have dual-boot capabilities again.

Thank you very much.

---

### Post by caljohnsmith on 2008-11-07
That's great news it's working. Cheers and have fun. :)

---

