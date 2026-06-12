---
title: "Problem booting Freebsd on usb flash drive"
date: 2008-09-08
forum: General Help
---

### Post by Jengajam2 on 2008-09-08
Flash Drive: 4 gigabyte Verbatim Store 'n Go 
Computer: Hp Pavilion a1640n
I was using unetbooting to create a flash drive boot for freebsd, but when I tried to boot it from the boot menu, I got a Grub error 15 and it went to the regular grub menu.
Any help would be liked.

---

### Post by zjagannatha on 2009-03-31
You probably need to change your BIOS settings as the computer is booting. If it's a newer computer then you should be able to set it to boot from a flash Drive.

I've had problems with GRUB and FreeBSD before. It seems that Grub can't mount the file system that FreeBSD uses.

---

