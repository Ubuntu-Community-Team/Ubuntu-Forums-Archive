---
title: "realtek alc880 spdif"
date: 2009-11-05
forum: Hardware
---

### Post by Infamshxr on 2009-11-05
Hello, I installed karmic and and need one of two issues fixed. I'd prefer to get the spdif output working but if not then I guess getti true stereo sound will work instead. Here's the problem, I have a tul ax480a7-f mobo with a realtek alc880 soundcard. Alsa picked up my drivers but when I run aplay -l it doesn't recognize that I have any digital coax ports. I have tried installing the realtek drivers from their site but got an error while either compiling it or doing the make command, can't remember but I do remember that it said it requires curses and that's where it stopped. Either way, idk why it doesn't even recognize the digital coax ports. If I can't get that the other issue is that when I go into the sound preferences and turn the balance all the way to the right I get no sound at all, like its in mono or something, but if its balanced at 0 I hear everything from both sides but it comes through all the speakers instead of just the side its supposed to. Please help asap! I will get working on it again in about 8 Hrs from now.

---

### Post by Infamshxr on 2009-11-05
oh, btw....

Northbridge chipset is ATI Radeon Xpress 200P
Southbridge chipset is ULI M1573

Maybe that might help some more. idk

EDIT: I also found this from another thread related to hardy. The person just added this to the end of his alsa-base.conf file:

options snd-hda-intel model=6stack-digout

If that worked for him, would that work for me? Allowing aplay -l to recognize my digital output instead of just the analog? If so, maybe a better idea to go back to hardy instead of karmic?

Ok, running the hardy live CD right now, not getting much further. I added that code to my alsa-base file. no such luck. here is the output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: M5461 [HDA ULI M5461], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Whats going on here???

---

### Post by Infamshxr on 2009-11-05
bump

anyone??? :-?

---

### Post by starfunker on 2009-12-20
I think I have the same problem, with the same card.  I have no digital capabilities and in the hardware section of the sound preferences, I think I've only got the crappy internal sound card that came with the computer showing.

results of aplay -l
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Any ideas how to sort this?

---

### Post by holmesy999 on 2010-04-10
after hours of searching, I finally get this thread, and note that problem isn't fixed - 

I have an old HP desktop computer, which now only has ubuntu 9.10 on it. everything I can do tells me that I have the ALC880 inbuilt sound on the motherboard
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00297771&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=465669&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00297771&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=465669&lang=en)


the computer has optical in/out on the back - I think you beauty I can connect this up to my amp and away we go. Nothing comes out of the cable to the amp.

I think that the issue is the same as people below - it is being treated as an analogue sound card and I can't find the digital out settings. I too have aplay -l saying  

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

shouldn't it say digital or something?

and when I go into alsamixer, everyone says to unmute the iec958 or something channel, but there is no such channel for me to unmute / mute - ie it doesn't exist. Right clikcing on the sound icon at the top of the screen, then sound preferences, output tab only displays that it is a internal audio analog stereo

This leaves me thinking either my computer is a big fat liar and doesn't really have optical out to pump sound into an amp (or I am a goose for thinking it did), or that I just can't get ubuntu to realise that I do have a soundcard which can do digital audio out

---

### Post by lidex on 2010-04-11
Install gnome-alsamixer, if not already:
```
sudo apt-get install gnome-alsamixer
```
Run it and go to the "Edit>Sound Card Properties" menu. Make sure all the IEC958 entries are selected. Close that. Now on the soundcard tab for the device in question enable IEC958.

---

### Post by lidex on 2010-04-11
As for alsa-base.conf options, here are what you can select from:
```
ALC880
======
  3stack	3-jack in back and a headphone out
  3stack-digout	3-jack in back, a HP out and a SPDIF out
  5stack	5-jack in back, 2-jack in front
  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
  6stack	6-jack in back, 2-jack in front
  6stack-digout	6-jack with a SPDIF out
  w810		3-jack
  z71v		3-jack (HP shared SPDIF)
  asus		3-jack (ASUS Mobo)
  asus-w1v	ASUS W1V
  asus-dig	ASUS with SPDIF out
  asus-dig2	ASUS with SPDIF out (using GPIO2)
  uniwill	3-jack
  fujitsu	Fujitsu Laptops (Pi1536)
  F1734		2-jack
  lg		LG laptop (m1 express dual)
  lg-lw		LG LW20/LW25 laptop
  tcl		TCL S700
  clevo		Clevo laptops (m520G, m665n)
  medion	Medion Rim 2150
  test		for testing/debugging purpose, almost all controls can be
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)
```

A stack represents an audio jack, so 3 audio jacks=3stack. 3 jacks + Digital out= 3stack-dig, etc. To the OP: never heard of tul but there is an option for tcl.

---

### Post by lidex on 2010-04-11
It would also help to install alsa-backports. Info is here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

If nothing helps you can try a full alsa upgrade by clicking the alsa-upgrade-script link in my sig.

---

### Post by holmesy999 on 2010-04-12
> **lidex said:**
> As for alsa-base.conf options, here are what you can select from:
```
ALC880
======
  3stack    3-jack in back and a headphone out
  3stack-digout    3-jack in back, a HP out and a SPDIF out
  
```A stack represents an audio jack, so 3 audio jacks=3stack. 3 jacks + Digital out= 3stack-dig, etc. To the OP: never heard of tul but there is an option for tcl.

I think this fixed it for me (although I did all your other steps as mentioned) - for some reason I found on another post that my alsa-base.conf file should be 3stack-dig (ie missing the "out" at the end) - but now I have all the iec958 to unmute, and now have music pumping into my amp - thanks heaps!

---

### Post by lidex on 2010-04-12
> **holmesy999 said:**
> I think this fixed it for me (although I did all your other steps as mentioned) - for some reason I found on another post that my alsa-base.conf file should be 3stack-dig (ie missing the "out" at the end) - but now I have all the iec958 to unmute, and now have music pumping into my amp - thanks heaps!

You're welcome. Enjoy.

---

