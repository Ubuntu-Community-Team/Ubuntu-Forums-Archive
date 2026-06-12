---
title: "Partition Name Change Problem"
date: 2008-08-18
forum: General Help
---

### Post by Goombie on 2008-08-18
I have a partition named "Documents" where I keep all my personal data. Recently, I rearranged my files a little, and changed the name of this partition from "Documents" to "PersonalStuff". The only problem is that the partition still shows as "Documents" in Nautilus, the generic "Open File" dialog, and the disk mounter applet on the Gnome desktop. Is there any way to change these so the partition shows as "PersonalStuff"? And on a side note, is there a way to name the partition "Personal Stuff" instead of "PersonalStuff"? I tried that in fstab, but I kept getting an error. Thanks!

---

### Post by Elcid247 on 2008-08-18
u can check to see if its label has actually changed or not by running

```
sudo mlabel -i <device> -s ::
```

i did have the same issue though, with my flash memory, but when i unmounted it removed it and placed it again, it got the label right...

try unmounting and remounting it and if tht doesnt work, log out and then back in or reboot.

---

### Post by mc4man on 2008-08-18
If it's an ext2/3 partition very simple to name/rename
One way is this - an ext3 partition  - /dev/sdb8
```
sudo e2label /dev/sdb8 TESTS_2
``` note _ to use 2 words
Just find out the sdxx of the partition first (partition editor , or sudo fdisk -lu if you don't know

For ntfs and fat32 I'd go into windows - administrative tools - disk management and r.click on the partition - properties and change volume label there

---

### Post by Goombie on 2008-08-18
Thanks for the ideas, folks. I should have mentioned that this is a FAT32 partition. :)

Elcid247: I tried that, but it just gives me an error: "unknown command: mlabel"

mc4man: Well, since I don't have windows, doing the disk management thing might be a problem. 

I also tried rebooting, but the name sticks around. :(

---

### Post by Too Late on 2008-08-18
You have to install mtools package (with Synaptic) to get that mlabel command.

---

### Post by Goombie on 2008-08-18
Ok, I have the mtools package installed, but I'm having trouble using mlabel. I can't seem to get the syntax for renaming quite right. :|

---

### Post by Too Late on 2008-08-18
I'm not using that program, but here is some instructions about that: [http://ubuntuforums.org/showpost.php?p=352645&postcount=10](http://ubuntuforums.org/showpost.php?p=352645&postcount=10)

---

### Post by Elcid247 on 2008-08-18
the code i gave u is for checking the name, not renaming it

this is the correct code for renaming it

```
sudo mlabel -i <device> -s ::PersonalStuff
```

this is the best reference for re-labeling

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

it shows u how to rename everything.

---

