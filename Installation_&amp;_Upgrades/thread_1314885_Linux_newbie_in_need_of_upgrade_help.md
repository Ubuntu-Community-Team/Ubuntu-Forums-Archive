---
title: "Linux newbie in need of upgrade help"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by chriscorbin on 2009-11-04
[FONT=Arial]I just started using Ubuntu on my HP mini 1000 laptop a couple months ago and i could not be more pleased with the results, in fact i decided to upgrade to 9.10.

However when i try to upgrade i get the message that i dont have enough free space on my hard drive. I have a windows XP partition that i havent used in forever, i was wondering what is the easiest way to erase the partition and encorperate it into my ubuntu partition?


[/FONT]Thanks in advance for the help

---

### Post by mkvnmtr on 2009-11-04
There is a program called gparted in the package manager. Download it and learn how it works. Do not try to use it on your system because it will only work on an unmounted disk. If you want to use it you might try it on another hard drive or ubc disk. When you feel comfortable with the program download the gparted live disk. Boot from it and you can do what ever you want to your hard drive.Be careful, ask all the question you need to before doing something and back up all your stuff.

---

### Post by flipper9 on 2009-11-04
Try PartedMagic...about the same as the gparted livecd, but much easier to use...

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by chriscorbin on 2009-11-04
> **mkvnmtr said:**
> There is a program called gparted in the package manager. Download it and learn how it works. Do not try to use it on your system because it will only work on an unmounted disk. If you want to use it you might try it on another hard drive or ubc disk. When you feel comfortable with the program download the gparted live disk. Boot from it and you can do what ever you want to your hard drive.Be careful, ask all the question you need to before doing something and back up all your stuff.


here is another question, since i dont have any data on this computer(i work on documents from USB drives and off our server) would it just be easier to reinstall ubuntu from the USB drive(this computer doesnt have a CD drive) if memory serves, there is an option in the installer to combine the partitions or totally re-format the whole drive?

I can just use a USB key to move the few documents i keep on this computer and create a live USB the way i installed ubuntu originally?

---

### Post by seenthelite on 2009-11-04
Yes, if you can download 9.10 and do a new install. Details are on the Ubuntu download page.

---

### Post by raymondh on 2009-11-04
> **chriscorbin said:**
> [FONT=Arial]I just started using Ubuntu on my HP mini 1000 laptop a couple months ago and i could not be more pleased with the results, in fact i decided to upgrade to 9.10.

However when i try to upgrade i get the message that i dont have enough free space on my hard drive. I have a windows XP partition that i havent used in forever, i was wondering what is the easiest way to erase the partition and encorperate it into my ubuntu partition?


[/FONT]Thanks in advance for the help

Hello ChrisCorbin,

Unfortunately, XP's disk management utility does not allow "shrinking".  I say this because you will have to get space from XP in order to add it to Ubuntu (something you know now).

You can use gparted from a live USB which will unmount the partitions.

Here is the link to gparted.  Kindly read through before proceeding.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

If you want to delete XP (as you posted),  you may have to edit your boot/grub/menu.lst to delete the XP entry so that you don't see XP anymore in the grub menu when you boot up.

Since you are working on partitions, why not take the opportunity to create a separate /home partition (which in Ubuntu contains your personal files and settings and config) that way should you need to re-install in the future, you can still retain them?

Post back if you need a mini-guide and if you decide to keep a dual boot or just sole-boot.  Also, share a screenshot of gparted to help the forum visualize.

As always, have a working back-up of your files.

EDIT : I type slow

---

### Post by chriscorbin on 2009-11-04
thanks for all the help guys

I have decided i only need Ubuntu and not XP, i moved the one document i had on the computer to our company server.

I am downlading the 9.10 live cd image to install, im just going to re-format the whole thing and install ubuntu, im assuming that wont give me any trouble


edit:
this may or may not be related but when i try to create a usb startup disk via the utility in system>administration

i get the error: "unable to determine the partition number."

---

### Post by cooper.z on 2009-11-04
> **chriscorbin said:**
> thanks for all the help guys

I have decided i only need Ubuntu and not XP, i moved the one document i had on the computer to our company server.

I am downlading the 9.10 live cd image to install, im just going to re-format the whole thing and install ubuntu, im assuming that wont give me any trouble


edit:
this may or may not be related but when i try to create a usb startup disk via the utility in system>administration

i get the error: "unable to determine the partition number."


It's better to upgrade or clean install ubuntu9.10. 
You will see some people, including me :( , are struggling on the new version.
Wait for anther 2 or 3 weeks.

---

### Post by seenthelite on 2009-11-05
You are on the right path now, from my experience you do not need to format the drive the Ubuntu installation will do this anyway to the default Ext4, which 9.10 uses.

---

### Post by chriscorbin on 2009-11-05
thanks for the help guys, works like a dream right out of the box, wireless, sound and all!

---

