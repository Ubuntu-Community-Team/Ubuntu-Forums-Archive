---
title: "keyboard sending ^[ (ESC character) before each letter on console login"
date: 2018-07-11
forum: Hardware
---

### Post by kevin160 on 2018-07-11
I have an HP Stream 7 (atom processor, 1GB RAM) tablet.  Usually, but not always, when I switch to console mode, I see extra ESC characters showing in the login like this:

login: ^[b^[e^[a^[u

If I simply ignore them and type my username and password, it doesn't let me in.  These extra characters do not appear if I drop to command line mode in grub.  They also don't appear once X has started up.  

Connecting a keyboard requires using a USB OTG adapter.  I use this adapter all the time on my Raspberry Pi Zero, and it works fine during the OS install to this tablet, so I assume it's not the adapter.  

I've tried quite a few distros, 4 different keyboards, with or without a powered hub.  

I've done dpkg-reconfigure for the keyboard, console-setup, locale, etc. settings with standard US and multilingual Canadian settings, etc.  

I'm trying to tune an install for this machine, trying different things (32 vs 64 bit for memory conservation, different desktops), and I really need access on the console.   

Has anybody seen this before?

---

