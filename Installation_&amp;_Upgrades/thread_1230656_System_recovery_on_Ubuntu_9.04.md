---
title: "System recovery on Ubuntu 9.04"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by pbjazzy007 on 2009-08-03
Help!!!  I've tried all the repair options and nothing is working!  I need the data (especially the VM's I've created via VirtualBox) and apparently I need to boot into it to back them up.  Is there a way to recover ubuntu 9.04 so that I can boot into it again?

---

### Post by mikewhatever on 2009-08-03
If the system doesn't boot, use a love cd/usb to copy the file to external storage location. Fixing a broken system is possible, but first one needs to know what's wrong with it.

---

### Post by pbjazzy007 on 2009-08-06
> **mikewhatever said:**
> If the system doesn't boot, use a love cd/usb to copy the file to external storage location. Fixing a broken system is possible, but first one needs to know what's wrong with it.
Well....It started when I tried to use VLC to watch an AVI video.  System crashed and I had to reboot.  This happened a few times until it was having problems booting into the system; GRUB locks up or the GUI appears scrambled.  Any ideas???

---

### Post by zietbukuel on 2009-08-06
> **pbjazzy007 said:**
> Well....It started when I tried to use VLC to watch an AVI video.  System crashed and I had to reboot.  This happened a few times until it was having problems booting into the system; GRUB locks up or the GUI appears scrambled.  Any ideas???
Use a Livecd as mikewhatever said.

---

### Post by thezood on 2009-08-06
> **pbjazzy007 said:**
> Well....It started when I tried to use VLC to watch an AVI video.  System crashed and I had to reboot.  This happened a few times until it was having problems booting into the system; GRUB locks up or the GUI appears scrambled.  Any ideas???

Yep. Boot from a Live CD, start grub by opening a terminal and enter:
```
sudo grub
```
In the prompt that appears, type:
```
find /boot/grub/stage1
```
That should return a location, for example hd0,0.
Now enter:
```
root (hd?,?)
```
where hd?,? is the location returned by the previous command. Now type this:
```
setup (hd0)
```
and
```
quit
```
to exit grub.
Now you'll have reinstalled GRUB. Let us know if you get any error messages or if the computer still doesn't start.

---

