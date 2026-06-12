---
title: "Black Screen of Death"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by teejay17 on 2007-12-02
I am having the worst problem with 7.10. (Ubuntu, Kubuntu, Fluxbuntu, it doesn't matter). It is this: once the distro is freshly installed, when I go to boot into the system for the first time, I'll get a blank screen right after the splash screen. I can't do anything. I can hear the system booting in the background, but for some reason I have a blank screen. The screen is illuminated, however, so it is not a hardware malfunction. 
This happens both when I do a fresh installation, or an upgrade from 7.04. 
Please help me overcome my dilemma—I can't reap the benefits of Ubuntu until this problem is solved.

---

### Post by messybricks on 2007-12-02
I had this same problem using the nvidia driver.  If I switch back to nv or vesa, it works fine... but no desktop effects :(

In case you don't know how to change drivers:

Once you are are logged in, hit CTRL-ALT-F1, and do sudo nano /etc/X11/xorg.conf

scroll down till you see 'Driver "nvidia" '.  Change this to "nv" or "vesa".

you can also do dpkg-reconfigure xserver-xorg if you prefer, but that takes longer.

If you can't get into the terminal window at all, try booting into recovery mode (hit escape to enter the grub menu on bootup)


Hope that helps

---

### Post by teejay17 on 2007-12-03
> **messybricks said:**
> I had this same problem using the nvidia driver.  If I switch back to nv or vesa, it works fine... but no desktop effects :(

In case you don't know how to change drivers:

Once you are are logged in, hit CTRL-ALT-F1, and do sudo nano /etc/X11/xorg.conf

scroll down till you see 'Driver "nvidia" '.  Change this to "nv" or "vesa".

you can also do dpkg-reconfigure xserver-xorg if you prefer, but that takes longer.

If you can't get into the terminal window at all, try booting into recovery mode (hit escape to enter the grub menu on bootup)


Hope that helps
Thanks. I'll give this a try.

---

### Post by Mze on 2007-12-03
Check this [thread]("http://ubuntuforums.org/showthread.php?t=629911") out if it would be of help.

---

### Post by teejay17 on 2007-12-04
Well, I figured out how to get my display working, but it doesn't have anything to do with the suggestions listed above. I'm not sure the reason, but here goes the description of what I did:
When Grub started to load, I pressed ESC. I booted into recovery mode, and after it did what it does (the loading, etc.) I simply put in the command startx. For some reason, this got things going and now I can reboot and have a working GUI. 
I'm not sure why this would be the case though; would anyone like to fathom a guess?

---

### Post by messybricks on 2007-12-04
I have no idea.  Maybe one of the things you tried was actually the real solution, but it needed a restart?  I doubt that's it, but that's all I can think of...

---

### Post by teejay17 on 2007-12-06
> **messybricks said:**
> I have no idea.  Maybe one of the things you tried was actually the real solution, but it needed a restart?  I doubt that's it, but that's all I can think of...
No, I had yet to try any of the solutions above. 
It's certainly strange...

---

### Post by messybricks on 2007-12-06
It was probably possessed.

---

### Post by SunnyRabbiera on 2007-12-06
No, I had a similar issue myself.
I think the error comes from usplash because as soon as you install Kubuntu desktop it goes away.
Of course your case is different, however I think its the default usplash of whatever you are using is what causes the issue

---

