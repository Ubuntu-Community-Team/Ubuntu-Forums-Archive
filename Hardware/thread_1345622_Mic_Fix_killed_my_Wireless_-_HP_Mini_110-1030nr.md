---
title: "Mic Fix killed my Wireless - HP Mini 110-1030nr"
date: 2009-12-04
forum: Hardware
---

### Post by pjsmetana on 2009-12-04
After initial installation of UNR 9.10, EVERYTHING worked beautifully except I had the same problem as every HP Mini user... the internal mic did not work (bug#458302). After tons of research I found how to fix it by installing the linux-backports-modules-alsa-karmic package through synaptic. I think opened terminal, $ alsamixer, tab, set front mic to 100%. All the sudden my microphone was perfect! 

...but that fix made my wireless card stop working. I reinstalled the drivers, and it said I had wireless, active and in use... according to everything except the top right meter icon that shows signal strength. This driver, Broadcom B43 is NOT the same driver that I had before the internal mic fix, and it also no longer shows the previous driver as an option. I have tried removing and reinstalling everything for wireless with no dice. 

I'm getting so frustrated with this, but I figure I should ask you guys here before I just dump it all, reinstall UNR, and forget about internal mic.

Anyone got a clue what I should do? I'm still fairly new to linux, so be gentle :)

---

### Post by ke4jgx on 2009-12-08
> **pjsmetana said:**
> After initial installation of UNR 9.10, EVERYTHING worked beautifully except I had the same problem as every HP Mini user... the internal mic did not work (bug#458302). After tons of research I found how to fix it by installing the linux-backports-modules-alsa-karmic package through synaptic. I think opened terminal, $ alsamixer, tab, set front mic to 100%. All the sudden my microphone was perfect! 

...but that fix made my wireless card stop working. I reinstalled the drivers, and it said I had wireless, active and in use... according to everything except the top right meter icon that shows signal strength. This driver, Broadcom B43 is NOT the same driver that I had before the internal mic fix, and it also no longer shows the previous driver as an option. I have tried removing and reinstalling everything for wireless with no dice. 

I'm getting so frustrated with this, but I figure I should ask you guys here before I just dump it all, reinstall UNR, and forget about internal mic.

Anyone got a clue what I should do? I'm still fairly new to linux, so be gentle :)


What i did to get mine working was this.. i installed the backportsthen installed the alsa mixer for gnome and needed dependencies thru synaptic then set the tab in alsa mixer thru the GUI with both mics enabled and it worked like a charm. I can now use skype under UNR no problem.

---

### Post by balls on 2009-12-16
I had this same issue and was able to fix it by reinstalling the wireless driver provided by HP using ndiswrapper.

Download this driver:
[ftp://ftp.hp.com/pub/softpaq/sp45501-46000/sp45515.exe](ftp://ftp.hp.com/pub/softpaq/sp45501-46000/sp45515.exe)

Extract it using cabextract

Use ndiswrapper to install the .inf file.

Hope this helped.

---

### Post by philidox on 2009-12-26
> **ke4jgx said:**
> What i did to get mine working was this.. i installed the backportsthen installed the alsa mixer for gnome and needed dependencies thru synaptic then set the tab in alsa mixer thru the GUI with both mics enabled and it worked like a charm. I can now use skype under UNR no problem.

Can you spell out as in step by step what you did.  I tried to follow your instructions and couldn't get it quite right.  I enable the backport thru software source and installed alsa mixer but all I got but the part were you say you install alsa mixru and needed dependencies thru synaptic I don't get because when I installed the alsa mixer the gui interface I got was basic and no settings for mics. Can you just dumb it down for me so I can follow your fix.  Thanks

---

### Post by hmn566 on 2009-12-27
Download the driver from hp site
extract in your notbook 
then follow this [https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

---

