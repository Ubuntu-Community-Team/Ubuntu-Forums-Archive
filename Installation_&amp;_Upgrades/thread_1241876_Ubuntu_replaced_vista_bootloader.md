---
title: "Ubuntu replaced vista bootloader"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by SGT Awesomesauce on 2009-08-16
HI, 
so yesterday i installed ubuntu 9.04 x64 on my computer and it works fine.  but for some reason it replaced the bootloader for my vista hard drive.  I have nearly 700 gb of data on that hard drive so reformatting is not an option.  I need to know how to get it to boot to windows without using the windows bootloader.  I already tried to use the windows system recovery and it just sat there detecting drives for like an hour.

---

### Post by mhgsys on 2009-08-16
You should edit your grub menu.lst 
And add the lines to boot vista.


first; open up a terminal and typ 
```

sudo fdisk -l 

```

This will give you a list of the partitions on your disks 
Look for HPFS/NTFS, this is your windows partition.

f.e  /dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS

Now you now where your windows is located, and we'll use that information to edit the grub menu.

EDIT THE GRUB MENU

in terminal typ:
```
gksudo gedit /boot/grub/menu.lst
```

Scroll all the way down to ### END DEBIAN AUTOMAGIC KERNELS LIST

and add;

```

title           Microsoft Windows 
rootnoverify    (hd0,0)
chainloader     +1

```

Save the file! 
Reboot, 
Option should be there and windows should be bootable


This example will work if windows is located on (hd0,0) (first partition on hda)


If it does not work for you post the outcome of sudo fdisk -l and we'll be able to help you.

---

### Post by SGT Awesomesauce on 2009-08-16
ok i made the changes and now im just waiting for some updates to be finished ill update if it works

---

### Post by presence1960 on 2009-08-16
it looks like you have more than one hard disk with windows and Ubuntu on separate disks, at least that is what I get from the original post. If that is true and the previous suggestion does not get Vista booting do this:

Boot into Ubuntu. Download from my signature line the Boot Info Script to your desktop. Once on the desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted here highlight all text and click the # sign on the toolbar to place code tags around the text.

This info will show us your setup & boot process. We then should be able to get Vista booting.

---

