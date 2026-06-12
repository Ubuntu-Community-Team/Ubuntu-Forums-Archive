---
title: "Boot / video and network issues on a Thinkpad R61"
date: 2008-07-21
forum: Hardware
---

### Post by lossfound on 2008-07-21
Hi there - I have a two-week-old R61i with integrated X3100 graphics and a 3945ABG wireless chipset. I was able to get Ubuntu Studio 8.04.1 installed on it, but I am having the following intermittent and increasingly common issues:

1) The machine gets to the X login screen, displays repeating-pattern gibberish, the screen turns on and off but ultimately stays black; "blind login" is not possible and the machine must be hard reset.

This initially happened about once every five tries but now happens 3 out of 4 attempts in plain ol' boot mode-- I switched to a "simple" GNOME login manager but it did not help. I can get to a login screen if I choose recovery mode at GRUB time, however, that leads to problem two:

2)About 30% of the time following a successful "normal" boot, and 90% of the time following a recovery-mode boot, the wireless card and my router have a communications issue. The SSID is identified correctly, signal strength looks good and the assigned IP address for the laptop looks good as well, but Ubuntu cannot seem to actually connect to anything or figure out the communications in any protocol-- DNS doesn't ever resolve and ping requests on the network are dead ends. My other laptop is running Hardy with identical settings and having no problems talking to the router so I don't think it's an issue with my authentication settings-- this one is really weird to me. 

I'm a newb, so I've been diligently searching... problem 1 seems to happen on slightly older T61s and R61s, but they all have discrete nVidia graphics and make login mgr sounds / allow a blind login. I can't find anyone having the startup trouble with an x3100 chipset. 

Have tried reinstalling Ubuntu, same thing. Help!

---

### Post by lossfound on 2008-07-22
Adding "nosplash" to the kernel boot parameters now seems to help both issues, but not 100% of the time.

---

