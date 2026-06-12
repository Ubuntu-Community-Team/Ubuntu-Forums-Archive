---
title: "Install Help - No CD - No Floppy"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by Infinity-1 on 2006-01-31
I have a Thinkpad 570 using USB CD (which is not recognized on bootup) and I have no external floppy drive.

Short of removing the hard drive and installing Ubuntu using a 2nd PC, can someone reply with instruction on how to write/start the bootloader/setup from a DOS prompt if i boot the laptop into DOS?

Thanks in advance.
Infinity-1

---

### Post by az on 2006-01-31
You probably can use loadlin to boot the install cd from windows.

[http://elserv.ffm.fgan.de/~lermen/](http://elserv.ffm.fgan.de/~lermen/)

You make a config that tells loadlin where the kernel and initrd is and what to use as the root filesystem (/dev3/sda1 for example) and you run it.

---

### Post by Infinity-1 on 2006-01-31
[QUOTE=azz]You probably can use loadlin to boot the install cd from windows.

[http://elserv.ffm.fgan.de/~lermen/](http://elserv.ffm.fgan.de/~lermen/)

You make a config that tells loadlin where the kernel and initrd is and what to use as the root filesystem (/dev3/sda1 for example) and you run it.[/QUOTE]


Thanks for the quick reply. Now I just have to figure out howto mount or refer to my USB CD. 

I will look at the loader from Slax again and try to figure it out. It has a dos loader that recognizes my usb CD drive. I just couldn't figure out how to transpose the slax location/initrd location to the Ubuntu location.

Wish me luck!

---

