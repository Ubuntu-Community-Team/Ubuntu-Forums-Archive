---
title: "all_generic_ide"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by Mark_in_Hollywood on 2007-08-21
I found 

all_generic_ide 

which is a grub 'command' to be added to:

/boot/vmlinuz-2.6.20-16-generic root=UUID=1f7fdc5e-fedf-4170-b281-989c00d37c11 ro quiet splash **all_generic_ide**

at: [http://ubuntuforums.org/showthread.php?t=527739&highlight=dvd](http://ubuntuforums.org/showthread.php?t=527739&highlight=dvd)

and want to know if that will work with my desktop computer? What does this command do?

The original poster has a laptop. I have never been able to get my cd-rw or dvd player to work properly. Feisty finds the cd-rw only if a disk it in the drive at power-up. And neither drive can mount. Even after sudo mount -a.

This has been this way since Breezy, no cd-rw and no dvd player.

---

### Post by Mark_in_Hollywood on 2007-08-31
Most unfortunate, that by following an "out of date" post, that I added the extra bit of code to the GRUB line. In another post I started about getting my DVD player to read, someone knowledgeable gave me a link about linux naming storage devices as SCSI for the sake of convenience.

If I had known that I wouldn't have added that line of code and potentially damaged my OS even further.

Thread Closed.

---

