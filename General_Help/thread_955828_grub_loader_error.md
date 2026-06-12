---
title: "grub loader error"
date: 2008-10-22
forum: General Help
---

### Post by zdiver07 on 2008-10-22
I installed ubuntu 8.04 64bit for amd proccessors on my external usb hardrive for my laptop, and it works fine and im highly satisfied with it.  But when i start the computer the grub loader gives me error 21 and i have to hit ctrl alt dlt and then it will work.  but if i do not have that external or my other external hooked up i can not load anything not even vista.  i want to be able to load vista without having to have the externals plugged in.  Please help!

---

### Post by phidia on 2008-10-22
You may want to consider reinstalling grub.

From your description it sounds like you installed grub to the external drive-or rather the installer itself installs to the MBR of the drive the install partition is on.

It might be easier to just use [Super Grub Disc]("http://www.supergrubdisk.org/") to fix this or you can follow the steps in the [wiki]("https://help.ubuntu.com/community/GrubHowto").

---

### Post by caljohnsmith on 2008-10-22
When you install Ubuntu to an external drive, by default it installs Grub to the MBR (Master Boot Record) of your internal drive since the internal drive is usually the default drive that boots on start up. But Grub needs its boot files on the external drive in order to work, so if you disconnect your external drive, you won't be able to boot at all. 

The most ideal solution is if you can set your BIOS to boot the external drive when it is present; that way you can restore your internal drive with a Windows MBR, and put Grub solely on your external drive. Then when the external drive is not connected, you can still boot directly into Windows on your internal drive. 

To restore the Windows MBR to your internal drive, you can use the Super Grub Disk that phidia linked to, or you can boot your Windows Vista Install CD and run:
```
bootrec /fixmbr
```
Then to put Grub in the MBR of your external drive, if you boot your Live CD and open a terminal (applications > accessories > terminal), just do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you run into problems. :)

---

### Post by zdiver07 on 2008-10-23
ok, so i did all of that used the vista disc to repair and the live boot cd to move the boot loader, it now boots fine if i dont have any usb drives plugged in but when i try to boot linux or vista from the grub loader i get,    error 21: selected drive does not exist  what now??

---

### Post by caljohnsmith on 2008-10-23
Go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. If your Grub menu is not too far off, that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to the (hd0,Y) that worked to boot Ubuntu. To boot Vista, at the end of the menu.lst add:
```
title	   Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
Reboot, try Vista, and let me know if it works. If it doesn't, then post the output of:
```
sudo fdisk -lu
```

---

### Post by zdiver07 on 2008-10-23
Ok, that got ubuntu to work but then when i tried to do the vista thing the entry didnt even show up when i got to the grub loader to load an os, and the original vista/longhorn loaders were still there but they still wont work.  Also when installed the ubuntu i had another external plugged in and if i have that external plugged in i get this error, NTLDR is missing    press ctrl+alt+del to reboot, which isnt a big deal i can just plug it in after i boot, but if theres a way to fix that i would like to do that.  Thanks again for all your help, here is the output of the sudo fdisk -lu



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce5973cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   139283549    69641743+   7  HPFS/NTFS
/dev/sda2       139283550   156296384     8506417+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   224829674   112414806   83  Linux
/dev/sdb2       224829675   234436544     4803435    5  Extended
/dev/sdb5       224829738   234436544     4803403+  82  Linux swap / Solaris

---

### Post by caljohnsmith on 2008-10-23
Based on your fdisk output, that previous entry I gave for Vista should work; if you aren't even seeing the new Vista entry in the Grub menu, then something must not have gone right when you edited your menu.lst. How about posting the output of:
```
cat /boot/grub/menu.lst
```

---

