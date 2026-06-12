---
title: "Ubuntu boot problem"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by cordlezz on 2009-09-21
Can anyone help me with this ?!

I can't boot into Ubuntu, I'm dualbooting and have installed Ubuntu through Wubi-installer.
I have 1 partition where I also have Vista installed, installed Ubuntu inside Windows.

I get "Try (hd0,0) EXT2" when I boot

This is my output from fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6059

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    5  Extended
/dev/sda2   *       38914       77827   312571904    7  HPFS/NTFS
/dev/sda5           37438       38913    11855938+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040e9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37459   300889386   83  Linux
/dev/sdb2           37460       38913    11679255    5  Extended
/dev/sdb5           37460       38913    11679223+  82  Linux swap / Solaris

Please help.

---

### Post by presence1960 on 2009-09-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


Edit: I just noticed you started a thread earlier about this same issue. Please do not create more than one thread about the same problem. Here is the link to your previously created thread: [http://ubuntuforums.org/showthread.php?t=1271612](http://ubuntuforums.org/showthread.php?t=1271612)

---

