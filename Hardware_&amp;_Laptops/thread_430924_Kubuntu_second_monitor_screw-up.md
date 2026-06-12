---
title: "Kubuntu second monitor screw-up"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by neilq101 on 2007-05-02
Hi, I recently installed Kubuntu Feisty, and having never been able to use multiple monitors on Ubuntu Edgy, I gave it a go, but in the Monitor and Display panel, when I set my desktop monitor as primary instead of the screen on my laptop, and then restarted the X server as it asked, the VGA attached monitor didn't detect. 

 Now when I start Kubuntu, it simply displays an empty terminal and won't respond to any typed commands; when I start in recovery mode, I am unable to start the X server again as it says it cannot detect a monitor.  I am aware of how stupid this mistake was, but can anybody tell me how to set my laptop screen as primary again?

My laptop is a Dell Inspiron 1300 with an Intel 915 chipset, which I was attempting to connect to a 19 Acer LCD monitor via my VGA-out port.
Kubuntu also seems to recognise my chipset as an i810 rather than 915, or at least is using the drivers for it (although Beryl and 915resolution work fine)

---

### Post by jack1254 on 2007-05-04
Hi, it sounds like your xorg.conf file got screwed up somewhere along the line. 

Boot into recovery mode, and first check to see if whatever you did made a backup of the configuration file. 

```
cd /etc/X11
ls
```

What you're looking for is something called xorg.conf.old or xorg.conf.backup, you get the idea. If it's there, restore it:

```
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
(Replacing xorg.conf.backup with whatever you found.

If there is no backup, try running the X11 Config. Utility
```
Xorg -configure
```
It will tell you where it put the file it generated, copy it to /etc/X11/xorg.conf
```
cp {path to file it found} /etc/X11/xorg.conf
```

Restart X/Computer.

---

