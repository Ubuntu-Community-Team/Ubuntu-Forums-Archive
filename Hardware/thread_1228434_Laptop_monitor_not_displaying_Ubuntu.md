---
title: "Laptop monitor not displaying Ubuntu"
date: 2009-07-31
forum: Hardware
---

### Post by Thor9 on 2009-07-31
I've just installed Ubuntu 9.04 on my laptop. Throughout the entire installation process I couldn't see one thing on my laptop's screen. I managed to install it by way of a KVM switch hooked up to my desktop monitor. I'm 100% sure my laptop screen works because I had windows xp running on it just fine. Are there graphical drivers I need to download? Please help
I have a Dell inspiron 1100 with 256 mb of ram

---

### Post by utnubuuser on 2009-07-31
Go to System>>Administration>>Hardware Drivers and see if there are any recommended drivers.

---

### Post by Thor9 on 2009-08-01
> **utnubuuser said:**
> Go to System>>Administration>>Hardware Drivers and see if there are any recommended drivers.

I checked and it said there are no more drivers needed. It still doesn't work. I've tried changing resolutions and everything I can think of.

---

### Post by captainskyhawk on 2009-08-01
There's a lot of problems right now with older Dell laptops and Ubuntu 9.04.

You can try going here and following the guide: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

If not, I'd recommend downgrading to 8.04.

---

### Post by captainskyhawk on 2009-08-02
You might want to try the fix found here:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/179503](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/179503)

It worked for me with the Inspiron 1100 and Ubuntu 8.04.3.

---

