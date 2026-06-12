---
title: "Headphone port - AO521"
date: 2010-11-14
forum: Hardware
---

### Post by qwertyface on 2010-11-14
Hi all,

I recently got the 64 bit 10.10 running on my AO521-105DK. 

The only trouble is, my Sennheiser headphones do not work when I plug them in. They work on other laptops and elsewhere so it isn't the headphones.

In fact, when I reinstall the OEM hard drive back in (with Windows Starter (=naff!)) the audio switches over just fine.

Has anyone encountered this at all: even better would be a solution?

Thanks,

QF

-------------------------------------UPDATE

On second look, I just found this: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer%20Aspire%20One%20521](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer%20Aspire%20One%20521)

It documents all of the same troubles that I am having (no surprise). So please ignore my original post, however, just out of curiosity, does anyone know when this is likely to be fixed?

Thanks,
QF

---

### Post by mrehorst on 2011-01-23
After hours of searching and trying many different things yesterday I got the headphone jack, microphone, and bluetooth all working, sort-of.

For the microphone and headphone jack you need to add the following two lines to the end of the /etc/modprobe.d/alsa-base.conf file:


```
options snd-hda-intel model=acer-aspire position_fix=1
options snd-hda-intel model=thinkpad
```


The first line fixes the microphone but for some reason the sensitivity is very low. You have to unlock the channel level sliders that control the mic level and set one of them to 0 and the other to 100% (in the pulseaudio volume control) or you won't get anything from the mic at all. The second line fixes the headphone jack completely.

Bluetooth can be made to work (also sort-of) by deleting the /lib/firmware/ath3k-1.fw and renaming file ath3k-2.fw to ath3k-1.fw

The Fn+f3 keys are supposed to allow selection of wireless, bluetooth, both, neither but it doesn't seem to work. Bluetooth and wireless will both be on after making the change listed above. I was able to pair a bluetooth earpiece and get audio working in both directions. I found this fix on a Russian blog which for which I've lost the link.

MR

---

