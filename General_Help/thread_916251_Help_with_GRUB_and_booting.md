---
title: "Help with GRUB and booting"
date: 2008-09-10
forum: General Help
---

### Post by xlostinlucidityx on 2008-09-10
I'm rather proficient in Windows, but when it comes to Linux, Im still learning. My hdd is dual booted UBUNTU and WIndows XP pro. When I try to run UBUNTU, it loads some grub command prompt. I pushe escape to boot and no matter what I choose it says "file not found." I don't know what to do but i have a file in that side of my harddrive that I NEED and I cannot reinstal ubuntu. THat file is very very important to me.

---

### Post by oilchangeguy on 2008-09-10
> **xlostinlucidityx said:**
> I'm rather proficient in Windows, but when it comes to Linux, Im still learning. My hdd is dual booted UBUNTU and WIndows XP pro. When I try to run UBUNTU, it loads some grub command prompt. I pushe escape to boot and no matter what I choose it says "file not found." I don't know what to do but i have a file in that side of my harddrive that I NEED and I cannot reinstal ubuntu. THat file is very very important to me.

run the computer from the live cd, and see if you can get your file that way.

---

### Post by xlostinlucidityx on 2008-09-10
see I don't even know what that is.

Since UBUNTU is free, i just downloaded an iso file and mounted it to an imaginary drive, intalling it within windows. It's worked fine for months now until yesterday.

---

### Post by kokkus on 2008-09-10
OK there are ways to fix your system. If your problem came after an update you can choose the last kernel on the grub list. If not, choose recovery mode, see if the system can fix the broken packages. Since the error comes up in system boot, I suggest u to overwrite the GDM file from your CD rom /etc/init.d/gdm.
When you are in grub, try shell > sudo --fix-missing 
If none of these tips works, start the cd installation in text mode and install only the booting files (includes grub display manager).

---

### Post by xlostinlucidityx on 2008-09-10
I would open in recovery mode but the grub opens before I am given the ability to open the menu and select that particular mode.

---

### Post by Ayuthia on 2008-09-10
> **xlostinlucidityx said:**
> I would open in recovery mode but the grub opens before I am given the ability to open the menu and select that particular mode.

I would start by booting from the live CD.  Select the option to run the liveCD but not install.  Once the desktop is loaded, go into the Terminal and type the following:
```
sudo fdisk -l
```
This will list out the partitions in your hard drive.  For example:
```

Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11111111

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22051   177123228    7  HPFS/NTFS
/dev/sda2           22052       42559   164730510    5  Extended
/dev/sda3           42560       43777     9783585    7  HPFS/NTFS
/dev/sda5           22052       25875    30716248+  83  Linux
/dev/sda6           25876       29791    31455238+  83  Linux
/dev/sda7           29792       33707    31455238+  83  Linux
/dev/sda8           33708       37623    31455238+  83  Linux
/dev/sda9           37624       38928    10482381   83  Linux
/dev/sda10          38929       42559    29165976   83  Linux
```
So if you are trying to access something from the linux side (let's say /dev/sda5), do the following:
```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```
This will create a folder for you called /media/sda5 where you can access the files that are inside of that partition.  You might be able to do the same with the Windows partition.  If it does not let you, you will need to mount it by trying (if sda1 is your Windows partition):
```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```This example will try to mount the directory by using the ntfs-3g filesystem type.  If ntfs-3g does not work, you might need to try ntfs.  This example is assuming that you already created /media/sda1 and that the filesystem is ntfs and not fat32.

You should be able to copy the file that you need.  I would recommend that you just copy the file(s) that you need, but not try to modify/create any files in there.  Once you have successfully copied the files out of the computer, you can then try and see if you can fix grub.

---

### Post by xlostinlucidityx on 2008-09-13
Thanks for all the help but I'm afraid I've really gotten nowhere. I'm going to attempt to re-burn the image file of UBUNTU onto a cd, and boot from it? Is this what u are referring to when you metion "live CD?"

Also, I have no idea which dev/sda?? my ubuntu bootup or file would be located. I know, I sound like a total noob right now, but when it comes to this I definitely am.

---

