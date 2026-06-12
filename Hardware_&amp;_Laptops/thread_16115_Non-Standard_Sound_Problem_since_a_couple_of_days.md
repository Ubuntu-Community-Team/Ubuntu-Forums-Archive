---
title: "Non-Standard Sound Problem since a couple of days"
date: 2005-02-19
forum: Hardware &amp; Laptops
---

### Post by rapha on 2005-02-19
Hi all!

I'm running two computers under the latest Hoary. One is a laptop, the other a desktop computer. On the laptop, all is fine. The desktop uses an onboard sound chipset (VIA 8235 with CMI9761 as per /proc/asound/cards) that is handled by the snd_via8cxxx driver. Up until a couple of days ago, sound was fine on the desktop, now it practically doesn't work anymore.

More specifically:
 
[list]
[*] Sound that is input through line-in will be properly output through the speakers
[*] Nothing that goes through /dev/dsp will be output, not even cat'ing a file works
[*] The channels shown in gnome-mixer are highly erratic, for both the ALSA and the OSS device. There isn't even a master volume for the OSS device.
[*] alsamixer shows a hell of a lot of channels, but even with all of them turned up will a sound emerge the speakers, apart from above exception with line.
[*] Choosing ALSA for an input system in the multimedia systems selector and trying to test that yields the error message "Test-Weiterleitung für 'ALSA' konnte nicht erzeugt werden", which should equal to "Test pipeline for ALSA could not be created" in English.
[*] Trying to test sound _input_ in the multimedia systems selector crashes it.
[*] Sound *does* completely work when trying with a Ubuntu Hoary Live CD. This is why I believe the sound hardware is physically working fine.
[/list]

I've tried reinstalling the entire operating system, compiling a custom kernel, recompiling alsa-utils, libalsa, or the alsa-drivers package, non of which helped.

Right now I'm back to a fresh installation of the latest Hoary on the desktop machine, so as to make receiving help a little easier.

Even the faintest pointers or suggestions highly appreciated.

Best regards from Germany,
Raphael

---

### Post by Erikhh on 2005-04-09
I cant help you, just tell, that I have excactely the same problem. And it worked fine in Ubuntu 4.

---

