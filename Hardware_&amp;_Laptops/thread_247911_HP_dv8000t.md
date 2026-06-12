---
title: "HP dv8000t"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by MadMatty on 2006-08-31
I just installed Ubuntu 6.06 (386) on my HP dv8000t laptop.  Installation went pretty smooth thanks to the forums/guides here.  What blew me away most is that while using the live CD, I decided to go ahead and install the OS.  I started the install but when it came to partitioning the disk (I wanted dual boot with XP), I wanted more info.  I was able to access the internet during the install!!!  Using XP, until the OS is installed all you have is an expensive box of parts; here you can actually use your system - amazing!

Now that I've gushed about this experience, I have a few questions ;).

1.  I have a dual core processor in my laptop, but in System Monitor it's only showing one.  Is it just the way it shows info, or do I need to tweak something?

2.  The LED for my wireless (which seems to be working just fine) flickers rapidly now whereas under windows it was always on steady.  Is this a common trait in Linux?

3.  How can I monitor my CPU temps?

Thanks for the help :D

---

### Post by hizaguchi on 2006-08-31
> **MadMatty said:**
> 
1.  I have a dual core processor in my laptop, but in System Monitor it's only showing one.  Is it just the way it shows info, or do I need to tweak something?
Install one of the SMP kernels.  There are different ones optimized for different architectures.  It'll be called "linux-somearch-smp".

---

### Post by MadMatty on 2006-08-31
I'm a noob at this.  Is that something I can do as an "upgrade" or is that a reinstall.  Thanks for responding so quickly.

---

### Post by hizaguchi on 2006-08-31
It's just a package to add.  You can use Synaptic or aptitude or apt-get, doesn't matter.  You just have to install the package and when you reboot it'll be in your grub menu.

---

### Post by MadMatty on 2006-08-31
OK, I used synaptic to install linux-686-smp, and now I have the choice in my boot menu.  When I attempt to boot to that I end up with this:

ALERT! /dev/sda2 does not exist.  Dropping to a shell!

Any suggestions (sorry about the hand holding)?

---

### Post by hizaguchi on 2006-08-31
That's weird.  /dev/sda2 sounds like a USB drive.  Is your Ubuntu installed on an external drive of some kind?  You don't get this error with the other kernel, right?

---

### Post by MadMatty on 2006-08-31
I have Ubuntu installed on a partition of my internal notebook hard drive.  This error doesn't occur during 386 bootup.

---

### Post by hizaguchi on 2006-08-31
Hmm, okie, check your /boot/grub/menu.lst file for any mention of /dev/sda2... probably in a kernel line down near the bottom.

---

### Post by MadMatty on 2006-08-31
I have to head to work.  I'll try that this evening.  Thanks for the fast replies. :)

---

### Post by MadMatty on 2006-09-01
Okay here it is:

tle		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.12-10-686-smp
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-10-686-smp
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

I just pasted the section describing the kernals.
:confused:

---

### Post by hizaguchi on 2006-09-01
> **MadMatty said:**
> root=/dev/sda2
That's weird.  I believe sda2 should be hda2.  It doesn't make sense that it would work for some kernels and not for others though.  You can change it temporarily at boot time by pressing "e" at the grub menu, then picking the kernel line and pressing "e" again, and then making the change and hitting "ENTER" and then "b" to boot.  If that works you can make it semi-permanent by editing the menu.lst, but it'll probably be overwritten whenever you upgrade the kernel.  Not sure why grub would want to use sda when it knows the root is hd0,1 (which is hda2).  

Before you try that though, it's interesting that your smp kernel is an older version than your regular kernel.  Did you install the package "linux-686-smp" or something with a longer name than that?  Because the "linux-whatever-smp" packages always depend on the latest kernel and should keep you up to date, and it looks like you've got an older kernel for smp.

---

### Post by MadMatty on 2006-09-01
I double checked in Synaptic, I installed linux.686.smp version 2.6.12.16.1 which is the latest (it says).

I went ahead and tried changing sda2 to hda2, but that just gave me the same error as before.

---

### Post by hizaguchi on 2006-09-01
I dunno what's going on then.  It's weird that your grub menu says sda instead of hda, but if changing that doesn't fix it it's over my head.  The only other thing I know to tell you is to make sure everything is up to date.  Synaptic tells me the latest 686-smp kernel is 2.6.15.24, so maybe your package database needs updating?  Try```
sudo apt-get update
sudo apt-get upgrade
```
to get everything as recent as possible, and if that doesn't fix it hope somebody smarter than my reads the thread. :)

---

### Post by MadMatty on 2006-09-01
I tried both of your suggested commands and got some failed to connect errors from the update servers.  I then let Automatix configure my repositories and then the latest kernal (the one you suggested showed up).  

Evidently that was the problem, because now I can boot up and both cores are available.  Many thanks again for all of the help!  :)

---

