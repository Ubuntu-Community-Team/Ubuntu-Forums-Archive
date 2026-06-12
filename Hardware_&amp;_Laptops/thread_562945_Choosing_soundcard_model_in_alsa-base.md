---
title: "Choosing soundcard model in alsa-base"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by Scynet on 2007-09-29
Hello.

I have a Fujitsu-Siemens Amilo M3438G laptop with a Realtek ALC880 soundcard. I've been trying to get my volume control wheel to work in Ubuntu Feisty according to [_these_]("https://help.ubuntu.com/community/HdaIntelSoundHowto") instructions, but so far nothing has worked. The problem is that I'm supposed to see the ALSA documentation for a list of soundcard types for my soundcard (Realtek ALC880). Well, the list is here:

```
ALC880
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
	  F1734		2-jack
	  lg		LG laptop (m1 express dual)
	  lg-lw		LG LW20/LW25 laptop
	  tcl		TCL S700
	  clevo		Clevo laptops (m520G, m665n)
	  test		for testing/debugging purpose, almost all controls can be
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)
```

I'm supposed to choose one that describes my laptop and then insert that name in alsa-base file:

```
options snd-hda-intel model=MODEL
```

However, I'm not sure which one to choose. Fujitsu-Siemens isn't mentioned in any of them. The laptop has 2 plugs on the side, one marked for mic, and the other says SPDIF/Headset. The instructions also note that I can add the following lines to the alsa-base file:

```
options snd-hda-intel probe_mask=1 
```
OR
```
options snd-hda-intel probe_mask=8
```

So, looking for the right combination randomly means I've got to reboot quite a few times, so if anyone could shed some light into the matter it would be greatly appreciated. I did all the steps in the instructions preceding choosing the type without errors. I'm newish to Ubuntu so please be clear. Thanks.

---

### Post by michael003 on 2007-10-17
Unfortunately if your laptop isn't listed you do have to basically try the different models randomly :-( It can be done without rebooting though. First make sure that nothing is using the soundcard (media players, and mixers (volume control) being the main culprits).
```
lsof /dev/snd/* /dev/dsp
```
If the above command shows no output, then nothing is using the soundcard. You can then unload the sound driver
```
sudo modprobe -r snd_hda_intel
```
and reload it and force a specific model
```
sudo modprobe snd_hda_intel model=MODEL
```

I would suggest starting with the 3stack models. From then on it's just random. Good luck!

---

