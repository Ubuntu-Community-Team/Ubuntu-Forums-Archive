---
title: "[SOLVED] Monitor problems w/8.04.1 (reposted)"
date: 2008-10-15
forum: Hardware
---

### Post by kcredden on 2008-10-15
Ok, I posted there was a problem with installing using a Samsung monitor, and I thought I was on 8.10, looks like I'm on 8.04.1 (according to the ISOs) so let me re-ask the question.

Tried to install Kubuntu 8.04.01 and every few minutes to seconds the monitor would blink off, and say something like "screen not optimized, need xxx resolution" The only way to get around this, is to turn the monitor on and off, then press the auto adjust button. 

It seems to have fully installed, but there may be a related problem. When it loaded, it looked - ugly - and reminded me of the old DOS GUIs back before Win3.1. Low colors, pixilated lines, etc. 

I thought I'd add also that I have both the alternative ISO and the standard. Would one of these cause the problems? (I can't remember exactly which I used. I used the Alt version on the T22 laptop, since Ubuntu has had no end of problems installing on it, but the alternative version worked like a charm. 

My system's specs are below. 

Thanks for any help
- Kc

1024mg memory
nVidia GeForce 7300 GS.
Primary monitor: Samsung SyncMaster 731n
2ndary monitor: IBM C72 CRT
Asus P5LD2 motherboard (not overclocked)
Intel P4 3.25ghz
Lite-On DVDRW LH20A1P (DVD+-RW DL burner

---

### Post by overdrank on 2008-10-15
> **kcredden said:**
> Ok, I posted there was a problem with installing using a Samsung monitor, and I thought I was on 8.10, looks like I'm on 8.04.1 (according to the ISOs) so let me re-ask the question.

Tried to install Kubuntu 8.04.01 and every few minutes to seconds the monitor would blink off, and say something like "screen not optimized, need xxx resolution" The only way to get around this, is to turn the monitor on and off, then press the auto adjust button. 

It seems to have fully installed, but there may be a related problem. When it loaded, it looked - ugly - and reminded me of the old DOS GUIs back before Win3.1. Low colors, pixilated lines, etc. 

I thought I'd add also that I have both the alternative ISO and the standard. Would one of these cause the problems? (I can't remember exactly which I used. I used the Alt version on the T22 laptop, since Ubuntu has had no end of problems installing on it, but the alternative version worked like a charm. 

My system's specs are below. 

Thanks for any help
- Kc

1024mg memory
nVidia GeForce 7300 GS.
Primary monitor: Samsung SyncMaster 731n
2ndary monitor: IBM C72 CRT
Asus P5LD2 motherboard (not overclocked)
Intel P4 3.25ghz
Lite-On DVDRW LH20A1P (DVD+-RW DL burner

Hi and sorry for moving your first post. :)
Have you tried booting into recovery mode which is usually the second choice from the grub. There you can use the xfix option to maybe correct the issues. If this gets you to a readable gui then you may use the alt, F2 keys and enter this command ```
gksu displayconfig-gtk
``` to adjust your monitor further.

---

### Post by cariboo on 2008-10-15
Have a look at this howto:

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

It should help you solve your problem.

Jim

---

### Post by kcredden on 2008-10-27
Thanks! That worked fine. I also found another work-around. The Kubuntu alternative installer (text based) elimates the install problem w/ the monitor, and all I have to do now, is immediately download the nVidia drivers upon startup. Depending upon your connection speed, it may mean about 5 - 10 minutes of the monitor fussing before it's fixed. 

Either works fine though. I may suggest that the Ubuntu community use the text based installer for good. V8 is the ONLY version I've gotten to work on any of my systems, in 5 years. *But only because I just now found the alternative installer. *

Sorry for the delay in writing, Been rebuilding my systems for Ubuntu. Now I can finally put Windows to rest for good :)

- Kc

---

