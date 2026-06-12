---
title: "Setting up windows in GRUB"
date: 2008-08-29
forum: General Help
---

### Post by danbrownlow on 2008-08-29
Hey there, 
I recently had to reinstall everything on my computer, so, as usual, I started by installing Windows Vista. I then used G-Parted resize the partition and then installed Ubuntu 8.04 on the space I created. The only problem is that I've broken windows and need to change the boot settings in GRUB, but when I opened /boot/grub/menu.lst, I saw no mention of windows. 

How do I change it so that Windows boots properly again?

Dan.

---

### Post by arch0njw on 2008-08-29
First, I would want to establish that you still have that partition.  Run gparted and see if the partition still exists.

Second, please post what your Ubuntu entry from the menu.lst looks like.  This may be a matter of manually adding an entry for Windows.

Check these sites for some ideas:
[http://www.linuxforums.org/forum/ubuntu-help/81524-i-m-having-trouble-my-grub-help-here-pls.html](http://www.linuxforums.org/forum/ubuntu-help/81524-i-m-having-trouble-my-grub-help-here-pls.html)
[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

---

### Post by danbrownlow on 2008-08-29
Okay, I followed what's on the links, and I've added some things, and the only thing I'm not sure about now is what hd(0,0) is? My Ubuntu partition are on hd(0,1), how can I find out where windows is?

Dan.

---

### Post by Too Late on 2008-08-29
hd(0,0) is the first partition, hd(0,1) is the second and so on. The first number inside brackets is the disk number (if you have only one disk, it's always 0) and the second number is the partition number (starting from 0).

I'm quite sure that your windows is on the first partition (hd0,0), but if you're not sure, post the output of "sudo fdisk -l" command here, or take a look at the partition names in gparted.

---

### Post by danbrownlow on 2008-08-29
```

255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34ef7da1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8950    71890843+   7  HPFS/NTFS
/dev/sda2            8951       11382    19535040   83  Linux
/dev/sda3           11383       19284    63472815   83  Linux
/dev/sda4           19285       19457     1389622+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x663e5845

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS


```

This is the output from "sudo fdisk -l" ^^

---

### Post by caljohnsmith on 2008-08-29
Since Windows is on sda1, all you should need to do to boot it is:
```
title Windows
root (hd0,0)
makeactive
chainloader +1
```
Just add that to your menu.lst. If you get any errors, tell us exactly what they are; since you used gparted to resize your Windows Vista, without using the Vista partitioner, the Vista partition table is probably broken. You'll probably have to fix it, but first see what happens with using the above.

---

### Post by danbrownlow on 2008-08-29
Ok, I added the lines to the menu.lst file and I got this message when I tried to load:

Windows failed to start. A recent hardware or software change might be the cause. 

1.Insert recovery CD... Etc...

File: \windows\system32\winload.exe
status: 0x0000225
Info: Missing or corrupt entry

Enter to continue..

It then asks me to select which OS. I chose Vista, and then went back to the previous screen.

---

### Post by arch0njw on 2008-08-29
I reread your original post.  I don't have experience with Vista, but I'm wondering if it is freaking out about the partition change.  Is it an option for you to reinstall?  If so, I'd reinstall windows first -- using the desired partition size, and then install Ubuntu in the remaining space.

---

### Post by caljohnsmith on 2008-08-29
> **danbrownlow said:**
> Ok, I added the lines to the menu.lst file and I got this message when I tried to load:

Windows failed to start. A recent hardware or software change might be the cause. 

1.Insert recovery CD... Etc...

File: \windows\system32\winload.exe
status: 0x0000225
Info: Missing or corrupt entry

Enter to continue..

It then asks me to select which OS. I chose Vista, and then went back to the previous screen.
Unfortunately, that's exactly what I meant when I mentioned that your Vista partition table is probably corrupt after using gparted. To fix it you'll need your Vista Recovery CD/DVD (if you don't have one you can download one [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/")), and run the following command from the recovery console/command line:
```
bootrec /rebuildbcd
```
Hopefully that's all it will take to fix Vista. Let me know how it goes, and if you need further info/details.

---

### Post by danbrownlow on 2008-08-29
Yea', I thought I might have to. I've just started using Ubuntu again, whilst I was using Mandriva, I got this error and all I had to do was change which partition Grub was trying to find Vista on.

Thank you for the help anyway, will try what you said now.

@arch0njw

I'm really not wanting to re-install /again/, I must have reinstalled Vista and various distro's about 10 times the last month. ¬.¬

---

### Post by danbrownlow on 2008-08-29
Hey, that worked fine thank you.

Cheers for your time and help. ^^

---

