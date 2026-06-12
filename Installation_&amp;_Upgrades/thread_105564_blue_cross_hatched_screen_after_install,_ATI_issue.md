---
title: "blue cross hatched screen after install, ATI issue??"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by bigern78 on 2005-12-18
HI Everyone,

I just installed the 5.10 AMD64 distro without any visible issues on my HP zv6201 lappy.  When I boot into the default is get a blurry grey then blue cross hatched screen (login screen?).  Anyone have any idea's where to start?  Anyone know the fix? 

Here are my specs

15.4" widescreen monitor with brightview
AMD 64 3200+
512MB RAM (one stick)
ATI Radeon Xpress 200M w/128MB RAM
Wireless B/G combo card (Broadcom chip)
4 USB 2.0 ports and 1 firewire port
60GB HDD
DVD +-R/RW (DL)
digital media reader.

Ubuntu 5.10 AMD64

Thanks for the help
BigErn

---

### Post by afhp on 2005-12-18
Not sure I understand what you describe, but it sounds like the default XWindow screen before the session manager takes over. Is GDM or KDM properly installed ? Or am I completely misunderstanding you ?

---

### Post by scpike on 2005-12-19
i have this same problem, but only after i have already logged in.

when i boot up everything is fine, and I can log into gnome.  but if i log out back to the login screen, everything is screwed up, and even if i log back into gnome its still screwy.

it almost looks like everything is being drawn over itself, theres a big thatchy pattern all over the screen

---

### Post by dsierpin on 2006-01-03
Hi all-

I've got an HP zv6000, and I had the same problems.

When you get to the GRUB menu, you have to boot the Recovery Mode option. Then, you find your xorg.conf file, (mine was at /etc/X11/) and cd to that directory. Open the file with:

nano xorg.conf


Find the section "DEVICE" that your video card is in. My video card is an ATI Radeon Xpress 200M. Add the following line:

Option "NoAccel"

Save the file with Ctrl-X, and reboot.

Hope this helps!

---

### Post by elephanthunter on 2006-01-21
Activating the NoAccel option does wonders, but I still get a hatched screen when I switch terminals or start Totem. Seems like restarting GNOME (ctrl + backspace) doesn't help out. :confused:

---

### Post by dsierpin on 2006-01-27
elephanthunter-

True, true.  You can either fix this by installing the vesa driver, or by downloading and installing the ATI fglrx driver.  Check out these HOWTO's by mlomker:

[ATI fglrx driver - latest]("http://ubuntuforums.org/showpost.php?p=423584")
[ATI fglrx driver 8.16.20]("http://ubuntuforums.org/showthread.php?p=408111")

For the vesa driver, just:

```
sudo dpkg-reconfigure xserver-xorg
```

And choose the vesa driver when it asks.  After I did this I had problems opening Totem still, but it didn't crash X anymore.  I finally got into X by choosing a different sink/source from the multimedia systems selector.  I'm at work right now, so I don't have Ubuntu in front of me.  But you can get to the mss through one of the panel menus.  Look for it, you'll find it.  Then, just mess around with the sinks/sources until you find a combination that works.  I hope that incoherent rambling helps.

---

