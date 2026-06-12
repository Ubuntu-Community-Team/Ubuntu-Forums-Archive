---
title: "CD-RW not detectable and problems after updating Feisty"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by gothica on 2007-06-03
Here's the story. So i just recently reinstalled ubuntu feisty on my ATA drive. After the installation process the system restarted and i looked at the grub boot list and it looked something like this:
-----------------------------------------------------------------------------
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=68e5f3ad-eed3-480a-b7b3-6e301d6c13f8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=68e5f3ad-eed3-480a-b7b3-6e301d6c13f8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```
-----------------------------------------------------------------------------

So i chose the first boot option and in a few minutes my freshly installed feisty booted for the first time. Right when i logged in, the system notified me to update which i did. **Note that at this point my second hard drive which is a SATA drive is still detectable and i was able to mount it and my internet connection works perfect, however my CD-RW drive is not detected**, which is funny coz i used my CD-RW drive when i installed ubuntu. After the update i was required to reboot my system which i did. Again, i looked at the grub boot list which now to my surprise looked something like this:
-----------------------------------------------------------------------------
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=68e5f3ad-eed3-480a-b7b3-6e301d6c13f8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=68e5f3ad-eed3-480a-b7b3-6e301d6c13f8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=68e5f3ad-eed3-480a-b7b3-6e301d6c13f8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=68e5f3ad-eed3-480a-b7b3-6e301d6c13f8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```
-----------------------------------------------------------------------------

Again,** i chose the new first option (Ubuntu, kernel 2.6.20-16-generic)**. This time though, it took a hell lot of time to startup my system. The boot screen eventually disappeared then text messages showed up. It took a lot of time like this, then about 15mins or so it booted. So i logged in. **This is when i noticed the problem. My SATA drive was no longer detected (it doesn't show on the Computer menu) and my internet connection was gone, however my CD-RW is now detected**. I checked my network settings (ifconfig) and to my surprise there was no IP address and all relevant info. I reconfigured it but its still the same. Now on my hard drive. I tried to see if its still there using fdisk but it hangs in the middle of detecting my hard drives. I had no choice but to reboot the system. When i rebooted, i opened the grub boot menu and chose the original boot option before applying the update (Ubuntu, kernel 2.6.20-15-generic). This time around, my system booted correctly. I logged in and everything is as it should be - my SATA drive is detected and my internet connection is working, however im back with my CD-RW not being detected. i checked whether my system is up to date and the update manager says it is updated. Likewise, to ease my pain i commented out all the "Ubuntu, kernel 2.6.20-16-generic" entry in my grub menu.lst and rebooted my pc. However, when i though of bringing it back to my boot list by uncommenting it in my grub menu.lst another problem showed. I tried to boot in again using the "Ubuntu, kernel 2.6.20-16-generic" entry, again it took a hell lot of time to boot but this time around, instead of getting me in a graphical environment, it showed me a terminal-like environment with the words "BusyBox v1.1.3" as its title.

So im wondering what is the problem with booting in the "Ubuntu, kernel 2.6.20-16-generic" and how can i resolve this? This issue is really frustrating me. I'll be hanging around the forums for the day in case someone replies right away.

---

### Post by gothica on 2007-06-04
it seems no has tried to help me yet. please can someone help me out?

---

### Post by gothica on 2007-06-04
does someone have any ideas about my problem or knows a link that could solve my problem? im searching the net right now but so far i have no luck.

---

### Post by gothica on 2007-06-04
bump!

---

### Post by gothica on 2007-06-04
im still stuck with this problem... i plan to recompile my kernel. i found a guide and im gonna try it out. i'll post here what happens. im still open for help though.

---

### Post by phidia on 2007-06-04
From reading through your post it looks like the update to the -16 kernel caused the non-showing sata drive. 
You could confirm this by selecting the previous kernel from the grub menu and if that is the problem then you can file a bug report at launchpad. There have been other similar complaints about the recent update. Please search the forums.

Or check the thread here: [http://ubuntuforums.org/showthread.php?p=2763724#post2763724](http://ubuntuforums.org/showthread.php?p=2763724#post2763724)

---

### Post by gothica on 2007-06-05
thanks for the reply.

i finally got everything to work. last night i recompiled to the lates linux kernel (2.6.21.3) and it did wonders for me. my ubuntu box is running at top speed and everything works fine. i suggest everyone who had problems with the kernel update to recompile to the latest one. the great guide that i used can be foune here [http://www.howtoforge.com/kernel_compilation_ubuntu?]("http://www.howtoforge.com/kernel_compilation_ubuntu?")

its a vey easy guide to follow that everyone can follow.i hope this helps.

---

### Post by kurraq on 2007-06-05
this is not the error of OS, just check your cables, definately you overcome the problem

---

### Post by phidia on 2007-06-05
> **kurraq said:**
> this is not the error of OS, just check your cables, definately you overcome the problem

Actually the update from the -15 to -16 kernel does seem to have caused difficulties with sata drives for some people-check the link I provided in my 1st post this thread.

---

### Post by gothica on 2007-06-08
has the ubuntu team realized this issue with the new kernel yet?

---

### Post by jharadie on 2007-06-08
I had the same problem.  I was playing with Feisty on a second box, at install everything was fine, found the CD-DVD, no problems.  After updating, lost it.  I searched the forums, and read stuff that said it was everything from bad cables to bad GRUB loader.  But I found a fix that works.

Since Ubuntu was on a second box, I just wiped and reloaded.  All fine after install.  Then, when Ubuntu wanted to install updates, I approved everything except the -16 kernel stuff.  Updated, rebooted, and I still had my CD-DVD.

Note that in the updates there is an automatic updater/installer, apparently works in the background.  The next time I rebooted, I noticed I was using the -16 kernel stuff.  However, I still have my CD-DVD.  I'm guessing it has something to do with the order of the updates/installs, I don't know.  What I do know is that by following the procedure of updating everything but the kernel, rebooting, then the auto updater updates the kernel, too, I keep my CD-DVD.

To be sure, and since I'm still experimenting with Feisty on a second box, I have repeated this procedure a few times.  It works every time.  FWIW, I'm happy enough that I'm going to go ahead and install Feisty on my main box (dual with XP).

J :D

---

