---
title: "for a &quot;minimal install,&quot; what to delete? (drivers, etc)"
date: 2008-06-04
forum: Hardware
---

### Post by stairwayoflight on 2008-06-04
Hello,

I just picked up an asus eeepc 4g. If I want a minimal ubuntu-server install, what is safe to delete? I want to install X, and maybe twm or fluxbox. I am hoping to be able to clean out some cruft such as unneeded drivers, etc.

So for a smaller kernel, I should recompile it based on my hardware. What can I get rid of re. X? After I install ubuntu-server, what can I delete? (I live in Canada/Eastern time zone, with a US keyboard layout.) Is there anything I should delete, like locales?

I will try to minimize writes to the drive, so I'll use ext2 and reserve .5g or so of ram for /tmp and /var/log maybe.

---

### Post by h4mx0r on 2008-12-10
Well I used this program called unetbootin to create a bootable usb. The program offers all sorts of distros and different iso to download of each it was really helpful. If you want a very minimal setup and able to configure it a lot I would recommend going with archlinux instead. There is an ubuntu eeepc wiki with tips on dealing with the smaller screen. And there is an archlinux wiki for dealing with the eeepc system settings for its individual drivers and stuff. I would recommend going with blackbox instead of fluxbox myself unless your planning some setup with the tab browsing feature. There is this 3rd party ubuntu derivative for eeepc that uses a weird clone of the xandros interface you might also want to check into. You might want to check which type of eeepc you have and to get it to boot from usb you have to remove the battery and power adapter then hook it up and press f2 when it starts to change the boot order so it loads from the usb.

---

### Post by h4mx0r on 2008-12-11
Try checking this site for a customized ubuntu based kernel to use, it has lot of drivers stripped from it so its minimal for eeepc. [http://www.array.org/ubuntu/about.html](http://www.array.org/ubuntu/about.html)

---

