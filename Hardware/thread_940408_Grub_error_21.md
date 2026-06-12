---
title: "Grub error 21"
date: 2008-10-07
forum: Hardware
---

### Post by catalax on 2008-10-07
Noob here.

My computer broke so i replaced the MoBbo. I have a dual boot system. Unfortunately I installed Grub on the windows disk, so I can't get windows to boot, and when i try to use the ubuntu disk on its own I get "error loading operating system" If it booted before with the different mobo, I don't understand why it wont go to grub now.

I can't gauruntee my hardware and bios is configured properly, Im trying to learn how to build the thing through trial and error. I imagine the first step to confirming that would be to make sure all the jumpers are set correctly on the mobo

---

### Post by cariboo on 2008-10-07
You seem to have a working computer, so I would suggest you download the [Super Grub]("http://www.supergrubdisk.org/") iso. I had to use it for a similar problem a couple of hours ago. It worked  to repair my grub problem.

Jim

---

### Post by catalax on 2008-10-07
I gave SGB a try. I can see that both Hard drives are being recognised but when I try to boot them up this is as far as im able to get.

[[IMG]http://img258.imageshack.us/img258/4299/xpid8.th.jpg[/IMG]](http://img258.imageshack.us/my.php?image=xpid8.jpg)[[IMG]http://img258.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

[[IMG]http://img243.imageshack.us/img243/9812/ubuntuzv3.th.jpg[/IMG]](http://img243.imageshack.us/my.php?image=ubuntuzv3.jpg)[[IMG]http://img243.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Sealbhach on 2008-10-07
Hi, try to restore grub using this method here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Quick process using the Live CD.



.

---

### Post by caljohnsmith on 2008-10-07
From those screen shots you posted, it looks like you are trying to boot the wrong drive for Windows. If you have your Live CD, boot it, open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
And lastly, to see which drive has Grub in the MBR (Master Boot Record):
```
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sdb bs=512 count=1 2>/dev/null | strings | grep -i grub
```
That should give us a better place to start for troubleshooting your problem.

---

