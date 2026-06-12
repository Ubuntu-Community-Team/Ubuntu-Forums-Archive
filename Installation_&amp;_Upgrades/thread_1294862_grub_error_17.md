---
title: "grub error 17"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by skanderon on 2009-10-18
I am a new user (noob), I want to install ubuntu and windows on the same machine, i.e. dual boot.  I have 3 hard drives
250GB IDE on IDE channel 1 (windows data only non boot)
80GB SATA on SATA 0 (win7)
80GB SATA on SATA 1 (unbuntu)
From previous windows installs I turned off the second ide channel to install both OS's.  Both went really well, but when I tried to turn on ide channel back on it gives me an GRUB error 17, when I turn it back off everything works fine.  I need the data on the IDE drive.  I searched the forums and tried the steps in some of the archived but no luck.

---

### Post by SteveDee on 2009-10-19
When you add or remove hard drives, the drive identities change. Grub error 17 is telling you that you are now pointing to the wrong drive in your grub menu.lst file.

There is some more info here: [http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368)

If you have 3 hard drives, and each has a single partition, the line in /boot/grub/menu.lst which defines the root drive will probably need to be either:-
root  (hd0,0)
...which is the first partition of the primary drive, or...
root  (hd1,0)
...first partition of the secondary drive, or...
root  (hd2,0)

If this does not make a lot of sense, try posting your menu.lst file here.

---

### Post by skanderon on 2009-10-19
Thanks, I checked out the other post as well, is there a way to rebuild the device.map or does it do that on its own?

---

### Post by bulldog on 2009-10-19
You can add your hdd to the device map with gedit.
```
gksu gedit /boot/grub/device.map
```

But that would be a minor issue.
You have to change your menu.list as well ,to get it to boot properly.
Your fstab will not have mount points for your partitions,and so on.

---

### Post by presence1960 on 2009-10-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

