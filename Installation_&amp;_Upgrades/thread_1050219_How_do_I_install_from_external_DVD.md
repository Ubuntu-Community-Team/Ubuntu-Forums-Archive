---
title: "How do I install from external DVD"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by sidewalkcynic on 2009-01-25
I have Windows XP on a 3Gb partition, and Ubuntu 7.04 on the remains of 10Gb.

I would like to install Ubuntu 8.10 (external DVD) over the 7.04.

My DELL Inspiron 7500 doesn't seem to be able to boot from the DVD, although the BIOS says it will. I don't know, maybe it has to be an internal DVD??? Anyway, I am trying as many different possibilities I can find.

It seems that if I load 7.04 in recovery mode, I get to a terminal line - is there code I can input to boot the external DVD to install?

---

### Post by taurus on 2009-01-25
There are other ways so hopefully one of them would work for you.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by sidewalkcynic on 2009-01-25
Thanks I'll be trying.

I don't think I completely understand the SMART BOOT; hopefully it will make sense when I get set up.

> Now we need to make a boot floppy. 

With Windows, use a utility called rawwrite. 

Format the floppy disk. For this you may open a command prompt (Start / Run / "cmd") and type format a: 

Then use rawrite command: rawrite -f sbm.bin (rawwritewin.exe sbm.bin) 
In Linux 
dd if=sbm.bin of=/dev/fd0

---

### Post by sidewalkcynic on 2009-01-25
I couldn't get past formatting the the disk.

The rawwrite stuff wouldn't go anywhere...

---

