---
title: "Wireless finally working. . .until I change screen resolution?!?!"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by Kibbo on 2006-03-27
Hi all, first post from a greenhorn.

Cliff notes:
Goal: 1280x1072 resolution, with wireless networking
-Ndiswrapper working.
-altered xorg.conf to enable more screen resolution options,  lost networking
- restored xorg.conf, networking back.

After much wailing and gnashing of teeth, I finally got my SMC2802 v.2 working with ndiswrapper.  Turns out Breezy was identifying it as a v.1, and trying to use native drivers which had to be cleared out.  I was online, surfing and having a great time.

Then, I wanted to change my screen resolution to 1280x1072, but the option wasn't available through the gui.  Searching for the problem, I found the command "sudo dpkg-reconfigure xserver-xorg" and went through the utility.  That fixed my screen problem, but eth0 wasn't showing up in ifconfig.  Ndiswrapper was still saying drivers and hardware present.

I restored xorg.conf file from backup, rebooted, and my network was back.  I tried to manually edit just the display settings in xorg.conf, and on reboot my network was gone again. Restore from backup, networking back.

I am using a Radeon 9800pro and a Samsung synchmaster 710v, 2.6.12-9-386 kernal.  I'm not sure which version of Ndiswrapper, I think 1.1.  

I thank you in advance for any help.

---

### Post by Kibbo on 2006-03-27
Issue resolved

I manually edited the xorg file again, a bit more carefully, restarted gnome and had them both up and running.  On reboot, I lost networking, but a second reboot resolved that.  I think the networking issues were unrelated to X.

---

