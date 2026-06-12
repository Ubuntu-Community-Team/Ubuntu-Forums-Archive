---
title: "rollback rx mbr problem"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by jv13613 on 2008-12-08
hi,
  i want to dual boot ubuntu with windows but i have rollback rx. i understand that it is installed in the mbr. grub will over write it. is it possible to move rollback rx to the volume boot record for windows. but could windows still boot. also, is it possible to put grub on a usb stick or cd that would chain load ubuntu without disturbing the mbr.

---

### Post by caljohnsmith on 2008-12-08
When you install Ubuntu, you could have Grub installed to the boot sector of the Ubuntu partition, and then after the installation you can make either a Grub CD, USB drive, or floppy to boot your Ubuntu. To do that, first install Ubuntu, but during the last stage of the installation process, click the "advanced" button, and then specify to have Grub installed to /dev/sda2 or whichever is going to be the Ubuntu main partition. After that, you could download and use the [Super Grub Disk]("http://www.supergrubdisk.org") to boot your Ubuntu, or you can even make your own customized Grub CD to boot Ubuntu easier; or if booting Grub on a USB stick appeals to you, I can help with that too. Just let me know which option you would like, and we can work from there. :)

---

### Post by jv13613 on 2008-12-09
i would like to use my usb stick.

Thanks

---

### Post by caljohnsmith on 2008-12-09
OK, were you able to install Ubuntu with Grub installed to Ubuntu's partition boot sector as I outlined in my previous post? If so, then how about opening a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
```
And be sure to have your USB stick connected so it will be detected by fdisk. With that info, I can then give you better directions for installing Grub to your USB stick.

---

### Post by jv13613 on 2008-12-09
i did not install ubuntu yet. i just want to plan it all out. i did a little research. i just have to copy the grub folder to the usb drive. then do grub root (usb drive name). then grub install

---

### Post by caljohnsmith on 2008-12-09
> **jv13613 said:**
> i did a little research. i just have to copy the grub folder to the usb drive. then do grub root (usb drive name). then grub install
The method I was going to give you is even easier; you don't have to install the Grub folder to your USB stick, you can just install Grub to the MBR (Master Boot Record) of your USB stick and point it to the Grub folder on the Ubuntu drive. That way you don't have to create a special Grub partition on your USB drive, and you won't have to manually update Grub's menu.lst when you get new kernel upgrades. It's up to you though how you want to do it.

---

### Post by jv13613 on 2008-12-09
i was wondering if you could do that. thanks

ps on an old computer i installed grub on a floppy.

---

