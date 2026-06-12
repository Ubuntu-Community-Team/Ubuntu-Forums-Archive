---
title: "Dual Win / Ubuntu Installation Problem"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by Rick Abraham on 2009-10-08
I have a PC with 2x HD's in it one 160GB drive and a 120GB drive.
I want to install Win XP onto one drive and Ubuntu on the other and choose which operating system I want to boot into when the GRUB menu loads.

I installed Win XP first onto the 160GB drive, all went ok.
Then I ran the Ubuntu installation disc and I installed Ubuntu onto the 120GB drive, with the following partations.

500MB    /boot ( boot flag ON )
8GB       swap area
20GB     /home
91.5GB  /

everything seemed to install ok, I got a popup during the installation asking me if I wanted to install GRUB onto the master boot record. It also said if Win XP was my only other operating system then it should be safe.
So I selected YES.
When the PC rebooted after the installation GRUB tried to load but gave me ERROR 21.

What has happened ? WHY ? and how can I fix this ??
Any help would be great.

---

### Post by zvacet on 2009-10-08
Maybe [this]("http://members.iinet.net.au/~herman546/p15.html#21") will help.

---

### Post by pawhtiobo on 2009-10-08
Hi :)

You can also try to fix your grub using [http://www.supergrubdisk.org](http://www.supergrubdisk.org).

See ya...

---

### Post by Rick Abraham on 2009-10-08
Hi guys ok I have downloaded and made up a SuperGRUBdisk CD but how do I use it and what do I do ????
I am absolutley a Linux NEWBIE LOL

I have Win XP installed on hd0,0 and Ubuntu is installed on hd1,0

I have a strange feeling that maybe in the boot list it thinks Ubuntu is installed on hd2,0 and Win XP on hd1,0 not sure.

Any help would be great

---

### Post by parrotred on 2009-10-08
i have a 3 hard disk
primary master as 60 gb seagate windows
primary salve 160 gb seagate data single ntfs partition
secondary master dvd-ram lg gh22
secondary slave 20 gb samsung ubuntu jaunty


I first installed windows and then unplugged that hard disk and installed ubuntu.
I have been using the system by removing either hard disk but now i would like to use both windows and ubuntu as dual boot.
i tried the following

sudo dd if=/dev/sdc1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work

so i tried this
sudo dd if=/dev/sdb1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work


Please guide me what should i do in order to dual boot with windows xp as the main and ubuntu as second.

---

### Post by jeremyswalker on 2009-10-08
Does the GRUB menu load? If it does, highlight the entry for windows and press 'e'. Write down what it says and post back here.

---

### Post by jeremyswalker on 2009-10-08
For your situation, parrotred, I would make the drive with jaunty on it the first boot drive. Then, I would add the following to /boot/grub/menu.lst on the jaunty filesystem:
```
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Of course, these settings assume the windows partition is the first partition on the first hard drive. You would have to adjust the '(hd0,0)' accordingly. The first number is the drive number, and the second is the partition number. Remember, GRUB starts counting from 0.

---

