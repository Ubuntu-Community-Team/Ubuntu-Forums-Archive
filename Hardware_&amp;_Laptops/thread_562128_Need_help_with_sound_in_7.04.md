---
title: "Need help with sound in 7.04"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by ddrplayer512 on 2007-09-28
I have a laptop and it sings with 6.06 and 6.10 but on 7.04, the sound support for my sound card broke or something. From looking at my laptop. I have an "Altec Lansing" card. Now when I look at the grub boot menu, I see a list of kernels to use to boot into Ubuntu, and it works on the 6.10 one, but not 7.04.
Now this is a serious problem because I need to reinstall Ubuntu and just want to start on the latest software.

Thank you in advance!:)

---

### Post by peabody on 2007-09-28
Altec Lansing may make sound cards, but from my understanding, they mostly make speakers.  Have you tried running the lspci command inside a terminal window?  That should list your internal interface cards which should tell you the exact make.

I had lots of trouble with my soundcard that was mostly fixed by manually installing the latest alsa:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
However, that was specifically for my soundcard (an onboard hda-intel).  Not sure if that'll help you or not.

---

### Post by ddrplayer512 on 2007-09-28
Unfortunately, I will have to install Fiesty right now so I'll check that out after installation and get back to you. Okay? :)

And, you're probably right, it says it on a speaker so I have no idea what the sound card is yet.

---

### Post by ddrplayer512 on 2007-09-28
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

That's one of the things that come out of the lspci command.

I'll read the guide you showed me to see if it works.

---

### Post by peabody on 2007-09-28
That's the exact audio controller I have, those instructions should do the trick.  Just be sure to use alsa version 1.0.14 and reboot after installation.

---

### Post by ddrplayer512 on 2007-09-28
Okay, Now I'm stuck at  the part where it tells you to "Manually Specify Module Parameters" I compiled the alsa parts and under this heading "Manually Specify Module Parameters" that's where I am lost.

Can someone explain this to me. Thank you to everyone so far.

---

### Post by peabody on 2007-09-28
You need to edit the /etc/modprobe.d/alsa-base file with root privileges.  You can do that with the following command run inside a terminal window:

```

gksu gedit /etc/modprobe.d/alsa-base

```

Add the following line to the very bottom of the file

```
options snd-hda-intel model=laptop
```

Save the file and reboot.

If that doesn't work you made need to change the model setting to something else (laptop-hp, lenovo, there's a couple of options).

---

### Post by ddrplayer512 on 2007-09-28
Sorry to keep asking you questions, but I have a Compaq v3000 and I tried that and put "compaq" where it says model=laptop. Is that the correct entry to put there?

---

### Post by ddrplayer512 on 2007-09-28
Also, I probably should have said this hours ago, but sound DOES play but extremely softly and I can listen using headphones.

---

### Post by peabody on 2007-09-28
Sorry about that, 'laptop' should be put there literally.  I could see how you might think I told you to replace that with some specific tag, but believe it or not, you'll probably have best results with that.

I have a compaq presario c571nr and when I first installed ubuntu, sound worked, but the speakers wouldn't mute when I plugged in the headphones.  This fixed it.

---

### Post by ddrplayer512 on 2007-10-01
It sadly still did not work. What is the difference between. 7.04 and 6.06 when it comes to sound, I wonder... Could it be something else?

---

### Post by peabody on 2007-10-01
I'm sorry about my previous advice.  Apparently there are a ton of different codec chips regarding hda-intel sound.  To figure out which is yours, run alsamixer in a terminal and see what chip it says it is.  Then, take a look at this excerpt from the alsa documentation and try different models for your chip.  My chips as a Conexant, though I'm not sure which because my chip name is something like CX20549 (Venice) which I had trouble matching to the below list.

Edit: I found out mine's a Conexant 5045.  The name apparently got changed around alsa 1.0.14: [http://suseforums.net/index.php?showtopic=28111](http://suseforums.net/index.php?showtopic=28111)

```
  Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    single_cmd  - Use single immediate commands to communicate with
		codecs (for debugging only)
    enable_msi	- Enable Message Signaled Interrupt (MSI) (default = off)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

	  Model name	Description
	  ----------    -----------
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
	  fujitsu	Fujitsu Laptops (Pi1536)
	  F1734		2-jack
	  lg		LG laptop (m1 express dual)
	  lg-lw		LG LW20/LW25 laptop
	  tcl		TCL S700
	  clevo		Clevo laptops (m520G, m665n)
	  test		for testing/debugging purpose, almost all controls can be
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC260
	  hp		HP machines
	  hp-3013	HP machines (3013-variant)
	  fujitsu	Fujitsu S7020
	  acer		Acer TravelMate
	  basic		fixed pin assignment (old default model)
	  auto		auto-config reading BIOS (default)

	ALC262
	  fujitsu	Fujitsu Laptop
	  hp-bpc	HP xw4400/6400/8400/9400 laptops
	  hp-bpc-d7000	HP BPC D7000
	  benq		Benq ED8
	  hippo		Hippo (ATI) with jack detection, Sony UX-90s
	  hippo_1	Hippo (Benq) with jack detection
	  basic		fixed pin assignment w/o SPDIF
	  auto		auto-config reading BIOS (default)

	ALC882/885
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  arima		Arima W820Di1
	  macpro	MacPro support
	  w2jc		ASUS W2JC
	  auto		auto-config reading BIOS (default)

	ALC883/888
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  medion	Medion Laptops
	  targa-dig	Targa/MSI
	  targa-2ch-dig	Targs/MSI with 2-channel
	  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
	  auto		auto-config reading BIOS (default)

	ALC861/660
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack with SPDIF I/O
	  3stack-660	3-jack (for ALC660)
	  uniwill-m31	Uniwill M31 laptop
	  toshiba	Toshiba laptop support
	  asus		Asus laptop support
	  asus-laptop	ASUS F2/F3 laptops
	  auto		auto-config reading BIOS (default)

	ALC861VD/660VD
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF OUT
	  6stack-dig	6-jack with SPDIF OUT
	  3stack-660	3-jack (for ALC660VD)
	  lenovo	Lenovo 3000 C200
	  auto		auto-config reading BIOS (default)

	CMI9880
	  minimal	3-jack in back
	  min_fp	3-jack in back, 2-jack in front
	  full		6-jack in back, 2-jack in front
	  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
	  allout	5-jack in back, 2-jack in front, SPDIF out
	  auto		auto-config reading BIOS (default)

	AD1884
	  N/A

	AD1981
	  basic		3-jack (default)
	  hp		HP nx6320
	  thinkpad	Lenovo Thinkpad T60/X60/Z60
	  toshiba	Toshiba U205

	AD1983
	  N/A

	AD1984
	  basic		default configuration
	  thinkpad	Lenovo Thinkpad T61/X61

	AD1986A
	  6stack	6-jack, separate surrounds (default)
	  3stack	3-stack, shared surrounds
	  laptop	2-channel only (FSC V2060, Samsung M50)
	  laptop-eapd	2-channel with EAPD (Samsung R65, ASUS A6J)
	  ultra		2-channel with EAPD (Samsung Ultra tablet PC)

	AD1988
	  6stack	6-jack
	  6stack-dig	ditto with SPDIF
	  3stack	3-jack
	  3stack-dig	ditto with SPDIF
	  laptop	3-jack with hp-jack automute
	  laptop-dig	ditto with SPDIF
	  auto		auto-config reading BIOS (default)
	
	Conexant 5045
	  laptop	Laptop config 
	  test		for testing/debugging purpose, almost all controls
			can be adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y

	Conexant 5047
	  laptop	Basic Laptop config 
	  laptop-hp	Laptop config for some HP models (subdevice 30A5)
	  laptop-eapd	Laptop config with EAPD support
	  test		for testing/debugging purpose, almost all controls
			can be adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y

	STAC9200/9205/9254
	  ref		Reference board

	STAC9220/9221
	  ref		Reference board
	  3stack	D945 3stack
	  5stack	D945 5stack + SPDIF
	  intel-mac-v1	Intel Mac Type 1
	  intel-mac-v2	Intel Mac Type 2
	  intel-mac-v3	Intel Mac Type 3
	  intel-mac-v4	Intel Mac Type 4
	  intel-mac-v5	Intel Mac Type 5
	  macmini	Intel Mac Mini (equivalent with type 3)
	  macbook	Intel Mac Book (eq. type 5)
	  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
	  macbook-pro	Intel Mac Book Pro 2nd generation (eq. type 3)
	  imac-intel	Intel iMac (eq. type 2)
	  imac-intel-20	Intel iMac (newer version) (eq. type 3)

	STAC9202/9250/9251
	  ref		Reference board, base config
	  m2-2		Some Gateway MX series laptops
	  m6		Some Gateway NX series laptops
	  pa6		Gateway NX860 series

	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF

	STAC9872
	  vaio		Setup for VAIO FE550G/SZ110
	  vaio-ar Setup for VAIO AR
```

---

