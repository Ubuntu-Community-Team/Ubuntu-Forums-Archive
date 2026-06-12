---
title: "Lock up with Ubuntu 9.10 and Intel GMA 950 video"
date: 2009-12-09
forum: Hardware
---

### Post by adammil on 2009-12-09
Hi all,

I am using Ubuntu 9.10 and I am getting lock ups after logging in usually within a minute at the desktop. Mousing around through the menus is enough to make it lock up. The system is totally frozen and I can't do anything but hard reboot.

It seems to be video related, how might I troubleshoot the cause? This system is a Compaq Presario with the Intel GMA 950 video chipset integrated on the motherboard and I just used the auto-detected video settings per the Ubuntu setup program.

Is there a crash log or anything else that I can post to help narrow the problem?

Thanks!
Adam

---

### Post by ManDay on 2009-12-09
I too have a GMA 950 and do have problems with it (just made a thread), but I don't get random lockups over casual actions. What's your other Hardware?

---

### Post by adammil on 2009-12-11
I have an Atheros based wireless card, but to eliminate it as the cause I removed that card and the problem occurs anyway.

---

### Post by ManDay on 2009-12-11
Ok, since I assume your computer is made of more than just a Intel GMA 950 Chipset and a Atheros WiFi-Card, why don't tell me about the rest?

---

### Post by snowpine on 2009-12-11
Lots of threads on this already; the "quick fix" is to disable Compiz desktop effects.

It is not an Ubuntu-specific bug; the exact same thing also happens to me with Arch and Fedora 12.

---

### Post by PaulReaver on 2009-12-11
does anyone else here use a mobile broadband dongle with their computers.

I have the gma950 and an atheros wifi card but it seems to lock up most often when use my mobile broadband dongle.  not a full crash just does'nt work until I remove the dongle. I think its either something to do with "usb devices" or the dongle specifically.

---

### Post by adammil on 2009-12-13
Ubuntu GUI starts and then locks up so fast after login that I don't have enough time to get to the command prompt to disable Compiz.

Is there a key sequence or anything I can use to abort the GUI loading so I am able to run the command line and disable Compiz?

Thanks!

---

### Post by adammil on 2009-12-13
I temporarily solve the lockups by doing Ctrl-Alt-F1 and then "killall compiz" and then Ctrl-Alt-F7 to go back to Gnome. That killed the window manager but was good temporarily. However, I never knew how you permanently turn compiz off. If anyone knows that answer I would love to know just for educational purposes.

In the end, I spent a few bucks for an NVIDIA GT220 video card and my problems have also been solved, leaving compiz on and everything being fine that way. Here's the detail how I installed it properly, special thanks to this post: 

[http://ubuntuforums.org/archive/index.php/t-281358.html](http://ubuntuforums.org/archive/index.php/t-281358.html)

1. Download Linux 32bit driver for the NVIDIA GT 220 driver from nvidia.com
2. Switch to ctrl+alt+F1
3. Kill X... Type this command - sudo /etc/init.d/gdm stop
4. Install the driver (from the /home/myname/downloads folder) - sudo ./NVIDIA-Linux-x86-160.42-pkg1.run
5. Restart X... Type this command - sudo /etc/init.d/gdm restart

Everything is working great now! I gave extra details there to help other Linux newbies like me.

Thanks all!

---

