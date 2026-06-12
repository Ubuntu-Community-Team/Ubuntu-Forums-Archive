---
title: "Cant login after first phase on Install"
date: 2005-01-27
forum: Installation &amp; Upgrades
---

### Post by eBast on 2005-01-27
Hello friends, this is my first post in this forum, and I am totally new to Ubuntu.  I downloaded and installed it on my Athlon XP 2000+, Asus A7N-266 VM board, 512 mb ram, Pixelview nVidia MX 440 display card.

The first phase of installation went on fine and I copied the whole cd to hard drive.  After rebooting, gnome desktop tried to start a couple of time, failed and I was left with a text  login prompt.

The problem is that it wont accept the user name and password that i had given during install. I had chosed LILO as the bootloader and with that my windows partition also is not bootable.

I would really like to try ubuntu, please help me out with the login problem

Thanks

---

### Post by Kopf on 2005-01-27
I would say your first mistake was installing LILO instead of GRUB, although LILO shoudl not cuase problems.  I would re-install Ubuntu with GRUB.  GRUB should automatically detect your Windows partition and setup an entry for it.   

It sounds like GDM isn't starting properly because X-Windows is trying to use the wrong video driver.  Let me know if this is still happening after the re-install.

Kopf

---

### Post by eBast on 2005-01-27
[QUOTE=Kopf] Let me know if this is still happening after the re-install.

Kopf[/QUOTE]

Ok will do that and revert here...

---

### Post by eBast on 2005-01-29
Reinstalled with grub... now i am able to get to login prompt at text mode, still no X.
Can boot my windows now..

I got this error message...

(EE) Unable to find a valid frame buffer device
(EE) NV(0) Failed to open frame buffer device

Fatal Server error
No screens found.

My hardware :

Athlon XP 2000+
Asus A7N 266VM
256 MB RAM
nVidia MX 440 64 MB

Please go through it and advice me further

If I should supply any further information, please tell me were to find it... and i will post it

---

### Post by Kopf on 2005-01-30
It sounds like X is trying to use the wrong driver for your video card.

type: sudo nano /etc/X11/XF86Config-4

Scoll down until you find a section named Device

Look at what is in the driver option. Since you have an Nvidia it should be nv.  If it isn't change it to nv.  You may also want to try vesa as a driver if nv doesn't work.  

You can also get the actual nvidia driver installed by following the directions found [Here](http://ubuntuguide.org/#installnvidiadriver) 

Hope this helps.

Kopf

---

### Post by eBast on 2005-01-30
Thanks all, I got it working after I installed the nVidia driver, all is fine now except some errors during startup, which I have posted as a new thread.

Thanks all for helping me..... :D

---

