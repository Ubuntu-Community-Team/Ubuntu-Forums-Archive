---
title: "Server edition install and USB key"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by dinonet on 2009-06-12
Hi, I'm looking at installing the latest ubuntu server edition. No GUI. Currently I have a Xubuntu gui install but I want to install from scratch using the instructions on installing using usb key. On the preparing files for usb page [https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html#usb-copy-flexible](https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html#usb-copy-flexible)
it talks about extracting this image to a partition on the usb drive # zcat boot.img.gz > /dev/sdX1
It says when I insert the usb key it should be mapped to /dev/sdX. I don't see that. The only way I can access it is by going to /media/disk directory. When I try to create fat16 partition using the instruction # mkdosfs /media/disk it gives me
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: unable to open /media/disk

Am I totally missing something? ANy help would be greatly appreciated

---

### Post by dstew on 2009-06-12
So you are running Xubuntu, and when you plug in the USB key, what happens? Can you see the USB key in the /media/disk directory?

---

### Post by dinonet on 2009-06-12
Yep. Then I saw that it could be /dev/sda but then I tried to add syslinux on it and it says I don't have that program I need to instal it blah blah and need the ubuntu disk. Is that the only way to get a bootable image on there so I can install 9x server edition?

---

### Post by dstew on 2009-06-12
If you know the device name for the partition is /dev/sda1, and if it already has a file system on it (you can read and write files on it) then you don't need to do mkdosfs. You need to do```
syslinux /dev/sda1
```for example if you want to install the image to the first partition.

By the way, the mkdosfs and syslinux commands will not work on a mounted disk. That is why```
mkdosfs /media/disk
```will not work.  The /dev/sda1 partition has been mounted to the mount point /media/disk. You have to unmount the disk, using the **umount** command, and then do the operations on the unmounted device. Just be sure that /dev/sda1 is the correct device name (the first partition on /dev/sda)

If it complains that you do not have syslinux installed, you can install it with```
sudo apt-get install syslinux
```Same for mtools.

You will probably also need to preface your commands with **sudo** to grant yourself superuser privleges that are required to do the kind of file system manipulations you are attempting:```
sudo syslinux /dev/sda1
```

---

### Post by dinonet on 2009-06-12
thanks dstew. I see what's going on now. The annoying thing now is that I can't install syslinux cos its asking for the CD and of course I don't have it. The updates don't work either cos I'm running 7.10. Can you give me a way I could install syslinux without needing to use the install CD?

---

### Post by dstew on 2009-06-12
If you have an internet connection, you can get it from the repositories. Even though 7.10 is no longer supported with updates, the programs should still be there.

If it wants the cd, you might need to remove or comment-out the cdrom line in your /etc/apt/sources.list file.

---

### Post by dinonet on 2009-06-12
Thanks again. One more question. I am installing ubuntu server. I've never used non-gui based systems before. Do I still need to install a firewall? How about antivirus?

---

### Post by dstew on 2009-06-12
I've never run a server connected full-time to the internet, so I can't say much about these. My guess is that a firewall is good. I have not heard of anti-virus for Linux. If you get software updates regularly, and follow proper security procedures (not running as root, good strong password etc.) I think you are OK.

---

