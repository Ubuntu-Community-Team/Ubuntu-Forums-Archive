---
title: "udev pchdtv 5500 dvb issue"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by fx303lee on 2006-11-21
Hello

I have a fresh install of 6.10 ubuntu server with a pchdtv 5500 dvb card in it.  The card chipset is detected and the modules load apparently correctly.  However, the /dev/dvb/adaptor directory is not created as it should be.  Rather, a /dev/.static/dev/dvb/adaptor is created with the correct devices for this card.  So, no apps can use the card because the devices don't exist in /dev/dvb - and symlinking this to /dev/dvb gives too many levels of symlinks.   

Does anyone have nay idea how to get this hidden /dev/.static/dev into the real /dev directory so the dvb device can be used? I've tried a bunch of scripts and hacks posted and none seem to work?

Thanks in advance
mike

---

### Post by Mercury821 on 2006-12-08
I am having a similar issue.  The card is detected but /dev/dvb directory is not created.  Has anyone figured this out?

---

