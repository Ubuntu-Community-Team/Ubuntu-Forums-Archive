---
title: "USB mouse only detected correctly at startup"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by IndigoMontoya on 2006-06-06
Hi.  I am using a Toshiba a45-s130 laptop.  My problem is that I use a USB optical mouse.  It works fine if it is plugged in the the computer boots, but if it is plugged in after boot the red light on the bottom, which is usually constantly on, flashes on and off.

when I plug it in dmesg says this:
   hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

clearly the cable is fine, because it works when in at boot.  Any thoughts?
I have a similar problem with a USB webcam, but am not as concerned with that.  Oh, a thumbdrive I use is recognized fine.  The mouse is Logitech USB optical mouse P/N 830524-0000.  I originally installed the server install (minimal) then did apt-get xubuntu-desktop and a day later apt-get ubuntu-desktop.  

I had the same problem in breezy. 

Thanks,
Scott

---

### Post by givré on 2006-06-06
[QUOTE=IndigoMontoya]Hi.  I am using a Toshiba a45-s130 laptop.  My problem is that I use a USB optical mouse.  It works fine if it is plugged in the the computer boots, but if it is plugged in after boot the red light on the bottom, which is usually constantly on, flashes on and off.

when I plug it in dmesg says this:
   hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

clearly the cable is fine, because it works when in at boot.  Any thoughts?
I have a similar problem with a USB webcam, but am not as concerned with that.  Oh, a thumbdrive I use is recognized fine.  The mouse is Logitech USB optical mouse P/N 830524-0000.  I originally installed the server install (minimal) then did apt-get xubuntu-desktop and a day later apt-get ubuntu-desktop.  

I had the same problem in breezy. 

Thanks,
Scott[/QUOTE]
I'm not sure, but which kind of kernel do you use actually, i guess it is the server one. If you use your laptop as a desktop now, you should consider a desktop kernel, it will fite better your need

---

### Post by IndigoMontoya on 2006-06-06
Here is my uname -a reply.

```
spruce@spruce-lap:/etc/init.d$ uname -a
Linux spruce-lap 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

```

Is that the correct kernle, if not how do you suggest I install a different one?  Compile it or apt-get.  I obviously prefer to use apt, but am comfortable and have compiled my own kernel several times before.

Thanks!

---

