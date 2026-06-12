---
title: "how to Synchronize updated ubuntu partition to the fresh one?"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by Freakonomist on 2009-10-25
hi there, i'm comer here, and new to ubuntu either. actually i have successfully installed ubuntu netbook remix to a usb external harddrive, then used it with my eee pc 1000h, boot from usb ext HD. and i also have updated the system and installed softwares from the repositories. it works well and up-to-date.
 now i want to install the same system into my main HD in my netbook, to make it dual boot with XP. and i already installed the fresh partition in my main HD, and the dual booting works just fine. but i have question about the updating,

can i just synchronize the updated packages from my updated USB harddrive to the fresh partition??...so i don't have to download the samething all over again.

if it is possible, how can i do it, and what tools should i use?

regars
Freakonomist

---

### Post by hogu on 2009-10-25
all the files you just installed should be on your usb drive, at this location

**var/cache/apt/archives**

you can copy those to your machine, and then, according to this thread;
 
[http://ubuntuforums.org/showthread.php?t=299447](http://ubuntuforums.org/showthread.php?t=299447)

sudo dpkg -i * should install everything

(I've never actually done it this way fyi)

but it should work.

---

