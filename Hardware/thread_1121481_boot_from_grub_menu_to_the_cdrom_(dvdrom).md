---
title: "boot from grub menu to the cdrom (dvdrom)"
date: 2009-04-10
forum: Hardware
---

### Post by linderox on 2009-04-10
I have a laptop with SATA. I just installed ubuntu 8.10 and I want to add line with a cdrom boot to the menu.lst, but I don't know how grub identify my cdrom in his rules.
can you give me some advices?

my /dev/cdrom -> /dev/scd0

---

### Post by meierfra. on 2009-04-10
Grub is not able to boot a cdrom drive directly. But grub  can do it indirectly using  SMB (smart boot manager):

[http://karuppuswamy.com/wordpress/2006/10/10/boot-cdrom-through-grub/](http://karuppuswamy.com/wordpress/2006/10/10/boot-cdrom-through-grub/)

---

### Post by teaker1s on 2009-04-10
You could also consider changing boot priority in bios to cd rom first then your hdd. Then unless you put a cd rom in it will boot to grub normally.

---

### Post by linderox on 2009-04-10
no, i have cdrom first, but i want to make one loader with all devices? how to do this with smb?

---

