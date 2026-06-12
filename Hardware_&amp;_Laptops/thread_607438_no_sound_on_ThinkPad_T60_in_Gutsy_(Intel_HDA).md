---
title: "no sound on ThinkPad T60 in Gutsy (Intel HDA)"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by gradedcheese on 2007-11-08
I can't seem to get audio working on my ThinkPad T60 in Gutsy.  So far I've checked that the mixer is set up correctly (not muted, etc), the Gnome sound control panel has 'alsa' as the playback option, and 'HDA Intel' is selected as the device, using PCM.  I rebuilt alsa using [these instructions]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") but that didn't seem to make a difference.  

Any ideas for what to try next?  My device is a 82801G, 00:1b.0 0403: 8086:27d8 (rev 02) and I'm running the vanilla gutsy kernel (2.6.22-14-generic)

Thanks!

---

### Post by trappist on 2007-11-09
Same problem here, same machine.  I'll post again if I find an answer.

---

### Post by Fire_Chief on 2007-11-09
I have a T60 that worked OOTB. When you run alsamixer, what chip does it say you have? I have an Analog Devices AD1981. Is yours the same? I've been working with someone on a separate thread who has an Intel HDA soundcard but the actual chipset is Conexant and it's not working under Linux.

---

### Post by trappist on 2007-11-09
Solved!
```
sudo apt-get install linux-backports-modules-generic
``` after enabling the backports repo.  Many thanks to [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by Fire_Chief on 2007-11-09
That's great information! Thanks for sharing :D

---

### Post by gradedcheese on 2007-11-10
Hmm... that doesn't seem to make any difference for me.  And yes, this one has the Analog Devices chip (AD1981).  

trappist -- so if installing from backports fixed it, can you tell me how you've set the alsa settings?

---

### Post by trappist on 2007-11-11
I'm not really sure that's the chip this thread is about, but to answer your question I ran alsamixer and the defaults were good.  I didn't touch them.

---

### Post by catfishk on 2007-11-11
if the modem is disabled in the Thinkpad BIOS, sound will not work

---

### Post by gradedcheese on 2007-11-11
Yes, I know about that (and the modem is enabled).  Hmm... I wonder what's up with my setup then?

EDIT:

> 
The issue was fixed in the latest development version of ALSA (1.0.15rc3), but Gutsy ships with 1.0.14.


...ah, but all of my alsa stuff is still 1.0.14, so I guess that the backports trick didn't help?  I'll see if I can get 1.0.15rc3 to install somehow.

---

### Post by Fire_Chief on 2007-11-11
Hmm..I'm running ALSA 1.0.14-1ubuntu2 as shown by ```
aptitude -V show alsa-base
```. Very strange that your laptop doesn't work despite it being the exact same hardware. The only thing I noticed (small but still) is that you've selected alsa as the playback device and I left it on Autodetect. Your setting should work fine...do you get any output when selecting Auto or other devices?

---

### Post by gradedcheese on 2007-11-21
Oh, how embarrassing!  This whole time the ThinkPad was in its docking station.  I took it out, pressed the physical sound "up" button, and now everything works fine.  Thanks for all your help though!

---

