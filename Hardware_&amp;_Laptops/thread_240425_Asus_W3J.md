---
title: "Asus W3J"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by Jmtan on 2006-08-20
Hi, I thought I might post my experiences on getting Ubuntu to work on a new ASUS W3J laptop. I hope it will help others who are complete newcomers to Ubuntu and Linux in general, just like me. :) 

Sound:
Probably the most major issue for me. If only I had seen this [link]("http://forum.notebookreview.com/showthread.php?t=57254") earlier. Here's the relevant quote: 
> 

Hi,
-Put "options snd-hda-intel position_fix=1 model=laptop-eapd" to "/etc/modprobe.d/alsa-base".
-Worked for me after reboot.

Processor:
Sometimes the processor constantly ran at maximum frequency even when idle, causing the laptop temperature to shoot up. I recommend you install a temperature sensor like this [one]("http://computertemp.berlios.de/"), in case this issue occurs.

No idea what caused the above problem to occur, but reinstalling Ubuntu fixed it for me. After that, I installed the linux-image-2.6.15-26-686 package from System->Administration->Synaptic Package Manager. It's in the Base System list. After that Ubuntu ran faster. However, the wireless card stopped working, so I had to install linux-686-smp package, found in Base System(restricted). Sorry I can't find the link where I found this info. :)

Video:
I couldn't get the correct resolution (1280x768) to display. Installing the ATI drivers from this [guide]("http://www.ubuntuforums.org/showthread.php?t=204910") and changing the resolution in System->Preferences->Screen Resolution worked for me. The refresh rate was changed to 75Hz, so I had to switch it back to 60Hz. I might have taken some other steps like changing the xorg-conf, can't really remember. :(

Touchpad:
To get scrolling support for the synaptics touchpad, I had to follow this [guide]("https://help.ubuntu.com/community/SynapticsTouchpad") on the wiki.

I think that covers it. I didn't work on the suspend issues or fancy stuff like xgl/compiz, as they're not critical to me. Now Ubuntu works better than my XP install, which can't detect my USB ports for some reason.

---

