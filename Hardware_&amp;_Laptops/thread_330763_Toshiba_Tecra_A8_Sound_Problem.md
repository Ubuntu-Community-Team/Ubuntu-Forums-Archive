---
title: "Toshiba Tecra A8 Sound Problem"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by cdburgess75 on 2007-01-03
Hello,

I have installed ubuntu 6.10 on my toshiba tecra a8.  All of it works:  sdcard, wireless, xgl, etc.

 But, I have no sound.  The speaker is in the upper right corner and it is not muted.  It all looks correct.

Where should I start?





/dave

---

### Post by raideen on 2008-02-28
I have a Toshiba Tecra A8-S8314. I had the same problem although I got sound through the head phones. The problem has persisted even through 7.10. I actually downloaded and installed the latest ALSA drivers, which didn't help. Here are the steps that I took after that. I probably didn't need the latest ALSA drivers. If you have no sound, this might not work for you.

I found some documentation of the various parameters for the snd-hda-intel module (for the sound card) at this [_kernel documentation site_]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt").

If you've researched this problem, you've seen people provide some configuration lines like "options hda-snd-intel model=blahblah". That works for some but not for others because although the hda-snd-intel driver is being used, there are various chipsets that are supported and each chipset takes different parameters. In my case, it was the ALC262. I was able to determine that by running alsamixer from a terminal (look for where it says "Chip"). Specifically, mine said "Realtek ALC262". You can also see this through the gnome-volume-manager (the sound icon). If you open that and go to File -> Change Device, one of them says "HDA Intel" and the other should show the chipset.

OK, now that you know your chipset, go to the web site and search for that chipset. In my case, I searched for "ALC262".

```
ALC262
		  fujitsu	Fujitsu Laptop
		  hp-bpc	HP xw4400/6400/8400/9400 laptops
		  hp-bpc-d7000	HP BPC D7000
		  benq		Benq ED8
		  benq-t31	Benq T31
		  hippo		Hippo (ATI) with jack detection, Sony UX-90s
		  hippo_1	Hippo (Benq) with jack detection
		  sony-assamd	Sony ASSAMD
		  basic		fixed pin assignment w/o SPDIF
		  auto		auto-config reading BIOS (default)
```

That's the list of supported "model" parameters (followed by a very brief description of each). I tried those models one by one. At the end of the /etc/modprobe.d/alsa-base file add a line such as the following:

options snd-hda-intel model=hippo

That's the one that happened to work for me. The fujitsu one gave me sound through both speakers and head phones but when I plugged in the head phones, I still got sound through the speakers. That gave me a lot of hope though so I just tried each one until it worked 100%. I hope this helps.

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by rhddallas on 2008-03-06
hey i have the tecra A8 sound problem too
i tried the guy-2-above-me's soultion but no luck. the file he told me to edit wont let me save. 
any way around that or a new solution? (yes i tried the one right above me too)

---

### Post by raideen on 2008-03-11
I should have mentioned that you need root privileges to edit the /etc/modprobe.d/alsa-base file. The easiest way to edit the file is to press <Alt><F2> and then type: gksudo gedit /etc/modprobe.d/alsa-base
If you can't get it to run, try it from a terminal window.

Alternatively, open a terminal window and then run: sudo nano /etc/modprobe.d/alsa-base

gedit is a GUI text editor. nano is a console text editor. You can substitute those with your favorite text editor. kate is simple if you're a KDE user.

---

