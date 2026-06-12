---
title: "Black Screen in ubuntu 9.04 x64 and 8.04.2 x64"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by Hans_Ritter on 2009-05-10
Hello, i'm new in this forum and recently i bought a new laptop. The problem is that, when i tried to install ubuntu 9.04 or 8.04.2 (both 64 bits), the instalation dont even start... i tried the alternate version of both ubuntus and nothing seems to work, i tried to set acpi off and other options and again the instaler refuses to start. My notebook uses a intel processor core 2 duo 5750 and 4gb memory ram, thats why i dont want tu use the 32 bits version (wich is installed and working fine). Sorry if my english is hard to understand, i'm brazilian and the portuguese forum simply could not help me. Thanks for your attention and please post any clues you have.

---

### Post by angellsl on 2009-05-10
Do you have any prompt screen showing the options for installation, does the splash screen appear and then screen goes black?

If so, could be your video driver problem. If your monitor doesn't support the horiz/vert rate set by default. Press Ctrl+Alt+F1, change /etc/X11/xorg.conf by adding "Driver vesa" in device section. Or refer to /var/log/syslog for detailed information

---

### Post by Hans_Ritter on 2009-05-11
> **angellsl said:**
> Do you have any prompt screen showing the options for installation, does the splash screen appear and then screen goes black?

If so, could be your video driver problem. If your monitor doesn't support the horiz/vert rate set by default. Press Ctrl+Alt+F1, change /etc/X11/xorg.conf by adding "Driver vesa" in device section. Or refer to /var/log/syslog for detailed information

angellsl, when i boot for the installation all the options apear, but when i chose any of them the computer don't start the installation, it just halt on a black screen with cursor blinking on the top left. About the video configuration, how is it possible that this can affect the instalation of ubuntu 64 bits? About the syslog, there's too much information for me to understand, do i have to look for any specif word ou line, will i find the any error message for my attempt to install ubuntu 64 there?
I tested the cd in my friend's house and it seems to load there and md5 check say the right numbers too.
Again, thanks for your patience and attention.

---

