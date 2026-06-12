---
title: "Installing Windows over Ubuntu"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by kartal on 2008-12-08
Hi

I need to install Windows xp over my current setup. I am not getting rid of Ubuntu :) I just need Xp for other stuff. I am sure installing Xp will mess up my boot loader. I am not very technical so i would like to know about the possible issues before starting installation. Here is what I have

-Macbook pro
-1 Macos working partition and installation
-Refit bootloader
-1 Fat32 empty partition
-1 Working Ubuntu partition
-1 Swap partition

So far I have backed up my ubuntu. I am not worried about messing up other installations like Ubuntu and Macos. I think it will be fine. I am just wondering about how to fix the boot loader and if I should expect anything on the MBR side. 

Most of the tutorials are on macos->xp->ubuntu. I could not find anything regarding this kind of installation pattern. I would appreciate any help or ideas. 


thanks

---

### Post by MobiusNZ on 2008-12-08
You're right about Windows buggering up your bootloader... even vista pretends no other os exists...

Basically you have to install windows then boot off a live CD to restore your old boot loader, which should be able to pick up windows and run with it.

---

### Post by RomanIvanov on 2008-12-08
Try this (in images for newbies) : [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by kartal on 2008-12-08
Hi

thanks for the answer. The only thing I am confused is the grub part naturally:) Am I supposed to install Grub on the Ubuntu partition or Xp partition?


thanks

---

### Post by caljohnsmith on 2008-12-08
It looks like in that tutorial that RomanIvanov linked to, the steps for reinstalling Grub are unfortunately not relevant to all situations. To reinstall Grub after you install Windows, first open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And that's all it should take. Let us know if you run into problems though. :)

---

