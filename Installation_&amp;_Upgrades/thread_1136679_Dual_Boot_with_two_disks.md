---
title: "Dual Boot with two disks"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by brotert on 2009-04-25
Hello there,

I'm new to the Ubuntu world and tried to install the latest version of Ubuntu. I have windows vista installed on one hard disk, and installed Ubuntu on another, empty hard disk. When installing, I selected the option to "Use Entire Disk" and installed Ubuntu there.

However, the computer boots directly into Vista and doesn't allow me to choose Ubuntu. Could Grub not have gotten installed? Anyone have any ideas on how to fix this?

Thanks!

---

### Post by graysky on 2009-04-25
You'll need to install grub to the MBR of your first disk or else the windows loader will come up first.  You'll also have to add a line to your grub's menu.lst to chainload the windows loader.  Example of my menu.lst:
```
default         0
timeout         5
color light-blue/black light-cyan/blue
splashimage /grub/arch-simplyblack-gts.xpm.gz

title           Arch Linux, kernel 2.6.29-ARCH
root            (hd1,0)
kernel          /boot/vmlinuz26 root=/dev/sdb1 ro quiet vga=773
initrd          /boot/kernel26.img

title           Intrepid Ubuntu GNU/Linux, 2.6.29.1-em64t
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.29.1-em64t root=/dev/sdb2 ro quiet
initrd          /boot/initrd.img-2.6.29.1-em64t

title           Jaunty Ubuntu GNU/Linux, kernel 2.6.28-11-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb3 ro quiet
initrd          /boot/initrd.img-2.6.28-11-generic

title           Windows XP Professional x64 Edition
root            (hd0,0)
makeactive
chainloader     +1

title   Arch Linux Native GRUB screen
root    (hd1,0)
chainloader +1

title   Ubuntu Intrepid GNU/Linux Native GRUB screen
root    (hd1,1)
chainloader +1

title   Ubuntu Jaunty GNU/Linux Native GRUB screen
root    (hd1,2)
chainloader +1
```

I haven't done it in a while, so do NOT take my suggestion as gospel, but FROM MEMORY, you have to use 'sudo grub-install (hd0)' to do this.  Again, do NOT run that command until some other folks can reply to your thread.  Google it too.

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

---

