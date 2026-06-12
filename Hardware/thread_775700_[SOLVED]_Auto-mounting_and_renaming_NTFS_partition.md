---
title: "[SOLVED] Auto-mounting and renaming NTFS partition"
date: 2008-04-30
forum: Hardware
---

### Post by SDL on 2008-04-30
Hi. I have edited my fstab to include the line:
```
/dev/sda1   /media/sda1   ntfs   user,uid=1000   0   0
```

I did this following [these instructions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions"). However, I didn't completely understand the instructions.

My HDD does automatically mount for my user just as I wanted but can I confirm that the way I've done it won't break anything? :p

Also, I would quite like to rename my partition, it is currently called '92.5 GB Media' which is a bit uninspiring! When I go to Places-> Computer and right-click on it and press rename, I get the error message: "The item could not be renamed. Sorry, couldn't rename "92.5 GB Media" to "sda1": Operation not supported by backend"

I have also tried to rename it using the same method but by going to Places-> Computer using ```
gksudo nautilus
``` to give myself root priveleges. I get the same error message.

Many thanks,

Stephen.

Edit: I guess "sda1" isn't much more exciting than "92.5 GB Media" but it's what I'm used to from Gutsy!

---

### Post by tyle on 2008-05-01
If your system boots and the HDD automounts I would say that everything is correct. When i have written something erroneous in fstab ubuntu refused to boot at all.

For the renaming issues, I followed the guide at:
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")
Just follow the instructions for NTFS and it should be fine. As far as i know there is no easy way to change the name of a HDD through the GUI.

---

### Post by Nepherte on 2008-05-01
You better mount your disk using UUID. It sometimes happens that another disk  is named /dev/sda1. So replace /dev/sda1 with UUID=yourdiskuuid

You can find the UUID of the disk by right clicking on the disk in nautilus and choose properties > volume

---

### Post by SDL on 2008-05-01
Hi. Thank you both for the replies. I have changed to use the UUID now. I can't change the name of the disk using the ntfs thing though. When I run 'mount' it says my disk it called "sda1" which I can change via the ntfs program but in 'Places' and 'Computer' my disk is still called "92.5 GB Media" but not to worry, I'm sure that I can get used to the new name!

---

### Post by blntechie on 2008-10-13
I also faced this issue and i tried many ways to solve it.
I did solve the issue with the help of other forums.

Steps followed:(i dont exactly remember the steps as i was trying many ways randomly...and something similar to this worked)

1) uninstalled ntfsconfig(if installed)
2) removed entries in fstab for auto mounting and saved(you can take a backup)
3) restarted ubuntu
4) Mounted all partition once
5) opened gparted and unmounted all partitions and checked the label values there.
4) closed gparted and added the removed entries again in fstab and saved
5) restarted ubuntu
6) And it worked!!! and all my partitions labeled appropriately now.

I'm not sure whether it works for others too... as i have seen in forums that one solution works for one and not for other for this problem.

I have attached screen shot of my Places/Computer after i tried these steps. Please let me know of any other steps tried and worked.

---

