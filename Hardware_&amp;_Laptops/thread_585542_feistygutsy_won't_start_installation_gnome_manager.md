---
title: "feisty/gutsy won't start installation gnome manager fall on Dell inspiron 6400 (0122)"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by frojnd on 2007-10-21
Ok here is the thing:

I just bought inspiron 6400 (0122) and I wanna to have ubuntu on it...

So i've put in Gutsy's cd. There were a couple of errors during loading kernel and than some moduls...

First error was: > FWH not detected.

Second one:>  */system-version no such file or directory
                     */biosversion no suc file or direcotry

4th one:  > bcm43xx: Error: Microcode "bcm43xx_microcode5fw" not detected or load failed

> And than finally is somekind of note: Running local boot script /etc/rz.load And after this note it try to start gnome manager but it fails and fais all over again... The same with feisty.


If there is anything I can do in bios or something please let me know. For bcm43xx erorr I found that this is some issue with wifi, so if I disable wifi in bios this error is gone, but there are still a few errors and most important one It can't start gnome manager.... 

Thanx in advance!!

---

### Post by frojnd on 2007-10-22
Well today I also tryed to install gutsy with alternate cd. Installation was good despite one or two errors. But gnome manager won't start AGAIN. But hey this time was system allready installed and when it was trying to start gnome manager and it couldn't I started a monitor and went into /etc/X11/xorg.conf and set resolution to 1024*768. So now I use Gutsy :)

---

