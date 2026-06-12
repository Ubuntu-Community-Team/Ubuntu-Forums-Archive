---
title: "Updates screw with NVIDIA module? A quick question."
date: 2009-01-29
forum: Hardware
---

### Post by Rendrago on 2009-01-29
First off, I already fixed my problem. I'd just like to know why what I did worked.

```
anonymous@computer:~$ uname -a
Linux computer 2.6.27-11-generic #1 SMP Tue Jan 27 23:53:21 UTC 2009 x86_64 GNU/Linux
```

The current install has be working as expected for the last few weeks. I let update manager download and install some updates today. Some, I believe were headers and other important kernel type stuff (The suspect).

I rebooted and got the low graphics mode options. I chose to look at the Xorg.0.log and saw:
**(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!**

I run dual GeForce 7800 GT's. I use the 180.22 drivers from Nvidia's site because of X window title bar issues. I also have to have the BusID in the xorg.conf or X freaks out with the two video cards.

In the xorg.conf it was still using nvidia (not nv). I started in low graphics mode and searched this site and Google. After reading for a while, I decided to try to re-install the drivers.

I downloaded the same 180.22 driver (run) file to my desktop. I did Ctrl+Alt+Backspace and then Ctrl+Alt+F1. I did sudo /etc/init.d/gdm stop and then ran the driver file.

After answering some questions, it (NVIDIA driver) said it was going to compile a kernel interface for the kernel. This is what I believe solved the problem.

After making sure the right xorg.conf settings were being used, I rebooted and got my nice shinny old desktop back, 3D acceleration and all.

Why did this happen? Why did a new nvidia kernel interface fix my problem?

Does doing what this guy says prevent it from happening again?
[http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu](http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu)

Thanks!

P.S. Please let me know if I need to mark this as solved or if I posted in the wrong place, etc.

---

### Post by AbdulRahiem on 2009-01-30
Same problem, but NOT entirely solved. Additionally, my wlan0 and ath0 network interfaces could not be seen. So, no access to router, no access to internet.

I did the same as Rendrago described. It restored my desktop, but not the wireless interfaces.

I rebooted to kernel 2.6.27.9-generic and now, there, my desktop was broken. So, I repeated the Rendrago steps in kernel 2.6.27.9-generic and everything was restored to working order, except: kernel 2.6.27.11-generic now boots to low graphics mode again and still no wireless interfaces working.

Unless there is some other solution, and I am only partly knowledgeable about using the command line so I would need detailed instructions, kernel 2.7.27.11-generic is a no-no for me until the problem is patched.

Meanwhile, I changed my grub script to boot to the '9' version as default.

Best regards

AbdulRahiem

---

### Post by Yashiro on 2009-01-30
> After answering some questions, it (NVIDIA driver) said it was going to compile a kernel interface for the kernel. This is what I believe solved the problem. Correct. The nvidia installer should recompile the binary blob that interfaces with your newer kernel. It didn't. A fresh install forces it to run at least once, apparently.

---

### Post by 3rdalbum on 2009-01-30
Modules (like drivers and filesystems and stuff) interact with the kernel through the use of an "ABI" - application binary interface. Often, when a new version of the kernel is released, the ABI will change (for various reasons that I won't go into here). Any old modules won't work as they don't know about the new ABI. You have to recompile them or, in the case of the Nvidia installer, just run the installer again so it can build itself with knowledge of the new kernel ABI.

If you say that the update you got had "headers and important kernel stuff", then you definitely got a kernel update. If you only used the Nvidia driver that's available through the Hardware Drivers program, you wouldn't have to do anything to get your card working again, as Ubuntu pushes out an updated recompiled version of its supported Nvidia driver.

I use a third-party wireless driver that sometimes won't work after an update, but the last couple of times I've been lucky and there hasn't been an ABI bump (or, I guess, not big enough to break my driver).

---

### Post by Rendrago on 2009-01-30
Thanks **3rdalbum**. That's exactly the information I was looking for.

---

### Post by AbdulRahiem on 2009-01-31
This morning (31/1) Update Manager upgraded from kernel 2.6.27.11-26 to 2.6.27.11-27 (lp #322553). It did NOT fix the problems described in this thread.

With regard to the ABI for my wireless card. I am out of my depth here. I have no idea how to identify the appropriate ABI and even less how to going about recompiling. Presumably, I can find all the information on this forum, but I'd be too scared ruining my system entirely.

Regards

AbdulRahiem

[COLOR=Green]**[SIZE=3]AbdulRahiem Dubelaar[/SIZE]**[/COLOR]
[I]PO Box 67363
43764 Bayan, Kuwait[/I]

---

### Post by AbdulRahiem on 2009-01-31
Actually, I am back in business now. I solved my remaining problem (no wireless; no internet) by running:

Code:
sudo aptitude install linux-backports-modules-intrepid
After rebooting I only had to do the nVidia bit, as per previous posts.

The 'ath0' interface no longer shows up, but who cares? It always seemed to be a copy of the wlan0 interface and that one is sufficient for my purpose.

Regards

AbdulRahiem

---

