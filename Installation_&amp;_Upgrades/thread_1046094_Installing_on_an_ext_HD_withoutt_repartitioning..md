---
title: "Installing on an ext HD withoutt repartitioning."
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by garlicsalt2 on 2009-01-21
Ok, so I have a 500 GB external USB & FW HD. It is formatted as Fat 32. I want to keep it that way!! I am an experienced Linux and Windows user.

I like the way that Wubi sets everything up on my ext drive, but I want to be able to boot directly from that drive into Ubuntu. I believe my two choices for booting Ubuntu from a fat32 drive are Syslinux, and GRUB4DOS. I don't mind using disk images, such as those used in Wubi, but I want to lose the Ubuntu boot entry when booting from my Windows drive.

Anyone know enough about boot loaders to help me out with this one??

Thanks,

--Aaron

---

### Post by Pumalite on 2009-01-21
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

---

### Post by garlicsalt2 on 2009-01-24
Ok. I have it working now. Thanks!
If anyone wants to know the details as to how I did it, I have them here.

GRUB4DOS needs to be installed from within DOS, so I followed these instructions:
[http://www.bay-wolf.com/usbmemstick.htm](http://www.bay-wolf.com/usbmemstick.htm)

**BIG, FAT WARNING!!! THIS _WILL_ *WIPE OUT* EVERYTHING ON YOUR EXTERNAL DRIVE.**

I just followed those instructions, and then installed Ubuntu 8.10 from within Windows XP, using the Wubi installer.

Next, I extracted the GRUB4DOS.ZIP file, found here:
[http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)
(Probably will want to use the latest one. I used the 2009-01-20 version).
I then rebooted from the external HDD, and then ran bootlace. Since I was booting from that drive, it was temporarily seen as the C: drive. So, I used
```
bootlace.com 0x80
```

Then, reboot back into windows, and replace the menu.lst file in the root of your external drive, with the file I've attached. (I had to rename it menu.txt, because UbuntuForums wouldn't let me upload a .lst file.) **BE SURE TO RENAME IT BACK TO menu.lst, and overwrite the one that is in the grub4dos.zip file**. I tweaked this file by hand. It works for me, but no guarantees!

If you have important stuff on your external drive, and can't stand to erase it, you should be able to do it with a Zip drive and disk, or with a separate flash drive. You would then need to use a different parameter to bootlace.com.

I wish you the best.

---

