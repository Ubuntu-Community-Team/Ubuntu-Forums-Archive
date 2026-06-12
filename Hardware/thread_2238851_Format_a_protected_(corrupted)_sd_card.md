---
title: "Format a protected (corrupted) sd card"
date: 2014-08-10
forum: Hardware
---

### Post by matteo14 on 2014-08-10
[COLOR=#000000][FONT=Arial]Some days ago one of my micro sd cards (a 32gb by Samsung) "decided" it is protected. It has no physical switch and I haven't found a way to format it yet. Every software I try to use on Windows says it is protected or read-only. I hoped GParted would have helped me but it didn't. I believe it's just a software problem but maybe this could be the end of sd. I want to know if it is definitely broken or not. Tthe sd is current in ntfs file system. What are exactly the command I should type in the terminal to format the sd? I read a lot on this forum and find similar threads but no one helps me.[/FONT][/COLOR]

---

### Post by erind on 2014-08-10
I had a similar problem (a read-only mode USB drive) a while ago and it turned out to be a broken USB. I had to return it (was within the warranty period). 

But first check the SD card health, run a few times a disk check from within windows, given that the SD card is formatted NTFS, see the results and proceed from there. Assuming no hardware problem, the disk checks will normally fix any file system inconsistencies. If the checks repeatedly fail then most likely you have a broken SD card. If the checks come clean then you can use GParted or any other partition tool you want. Make sure you run the disk checks a few times.

Running GParted or any other tool for that matter won't help, if the hardware is broken. As for running any command from the terminal won't change anything either, after all GParted and other Linux GUI tools are front-ends of precisely these terminal commands. 

However from the looks of it, it seems to be a hardware problem, maybe it's time for a new one.

---

### Post by redrumrogue on 2014-08-11
If you don't care about any data on the card I'd be tempted to try wiping the card with dd and then formatting it.

sudo dd if=/dev/zero of=/dev/<your device> conv=noerror

or to wipe just the first 1GB ...

sudo dd if=/dev/zero of=/dev/<your device> bs=1M count=1024 conv=noerror

Be careful to set the correct "of" device :-)

---

