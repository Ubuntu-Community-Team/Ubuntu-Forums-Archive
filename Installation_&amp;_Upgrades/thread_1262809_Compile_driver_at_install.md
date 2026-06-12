---
title: "Compile driver at install?"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by jdmagoo on 2009-09-10
Hello,

I am trying to install Ubunto onto a hardware RAID setup however it does not seem to see my drives so which seems to be a driver issue, is there any way to compile a driver at install? since I can't seem to find a drive for my card (Promise Supertrack EX6850 oem Vitesse VSC7250)

Thanks for any help!

---

### Post by jdmagoo on 2009-09-10
bump ^^^^

---

### Post by Whiffle on 2009-09-10
Looking at the kernel config for the kernel on my laptop, it looks like that driver is compiled as a module named "stex" by default.  Which install CD are you using?

---

### Post by jdmagoo on 2009-09-11
Ubuntu Server 9.04 AMD64

---

### Post by Whiffle on 2009-09-11
Hmm.  What I would do is boot the install cd, and then when you get to the screen after the cd has booted ([!] Choose Language), hit ctrl+alt+f2, hit enter to get a terminal, and then run "lsmod"  The module stex should appear in that list, if not, do "modprobe stex" and then do "ls /dev/sd*" and hopefully your drive will be listed.

---

### Post by jdmagoo on 2009-09-11
Thanks, I actualy just managed to get it to work, it seems my array wasn't build correctly... stupid me, Oh well thanks for the help.

---

