---
title: "[SOLVED] mic sound now thru all speakers, internal or not...."
date: 2008-08-07
forum: General Help
---

### Post by desideratha on 2008-08-07
I am completely frustrated...

Now a new problem, mic is now sounding thru my speakers and headphones at the same time!
and BEFORE I could never plugin my headphones without the sound still going thru the internal speakers!



plaase help

---

### Post by DagMan on 2008-08-07
have you searched the forum or googled for what you got from terminal when you identified your soundcard?
What have you tried so far that didn't work?

---

### Post by Crafty Kisses on 2008-08-07
Calm down, and post the following output:
```
lspci
```
Not sure if you know this, you have to have patience with Linux. :KS

---

### Post by prshah on 2008-08-07
> **desideratha said:**
>  I am about to erase THE WHOLE THING and go back to my stable vista-..

That's probably a good idea; you can also shred the ubuntu-studio cd while you are at it... ;)


> **desideratha said:**
> 
the mic is now sounding thru my speakers and headphones at the samwe time! and BEFORE I could never plug in my headphones without the sound still going thru the internal speakers!


Looking at your previous posts and noting the headphone problem, the obvious inference is that you have changed some settings; can you give more background information on what you've already done? Or has it changed by itself?

---

### Post by desideratha on 2008-08-07
Thank you guys, I know I lost my nerve last night...

The one thing I changed was the Alsa-base last two lines to:

options snd-hda-intel model=vaio

as suggested by a user with similar problem.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by DagMan on 2008-08-07
is there a specific model number, like vaio vgn-s4 or vaio-sz61 etc.

---

### Post by desideratha on 2008-08-08
Vaio Vgn-n250

---

### Post by DagMan on 2008-08-08
Yeah I see your frustration better now with zero google hits on that.

The most common option for vgn in general was 
options snd-hda-intel index=0 model=vaio
and also
options snd-hda-intel model=auto
but there were a lot of differant ones.

Here's the wiki page for snd-hda-intel [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and specifically, if you can't get the problem solved and want to persue it further then the last thing to try will be following "Update to the Latest Version of ALSA" on that page, and hopefully you'lle be able to  build the most recent modules tools and libraries.  You need matching versions.  If you screw it up you can rebuild the normal alsa modules using module assistant.  You'de search the forum for 'alsa module-assistant' and hopefully it would save time.

Good luck.

Before you go rebuilding though here's a list of the model names that can be passed to the module in the hardy modules.  Many of them are redundant, I'm just copying and pasting.  There isn't much there for vaio or sony but something else might work for you.
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
	  will		Will laptops (PB V7900)
	  replacer	Replacer 672V
	  basic		fixed pin assignment (old default model)
	  test		for testing/debugging purpose, almost all controls can
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC262
	  fujitsu	Fujitsu Laptop
	  hp-bpc	HP xw4400/6400/8400/9400 laptops
	  hp-bpc-d7000	HP BPC D7000
	  hp-tc-t5735	HP Thin Client T5735
	  hp-rp5700	HP RP5700
	  benq		Benq ED8
	  benq-t31	Benq T31
	  hippo		Hippo (ATI) with jack detection, Sony UX-90s
	  hippo_1	Hippo (Benq) with jack detection
	  sony-assamd	Sony ASSAMD
	  ultra		Samsung Q1 Ultra Vista model
	  basic		fixed pin assignment w/o SPDIF
	  auto		auto-config reading BIOS (default)

	ALC268
	  3stack	3-stack model
	  toshiba	Toshiba A205
	  acer		Acer laptops
	  dell		Dell OEM laptops (Vostro 1200)
	  zepto		Zepto laptops
	  test		for testing/debugging purpose, almost all controls can
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC662
	  3stack-dig	3-stack (2-channel) with SPDIF
	  3stack-6ch	 3-stack (6-channel)
	  3stack-6ch-dig 3-stack (6-channel) with SPDIF
	  6stack-dig	 6-stack with SPDIF
	  lenovo-101e	 Lenovo laptop
	  eeepc-p701	ASUS Eeepc P701
	  eeepc-ep20	ASUS Eeepc EP20
	  auto		auto-config reading BIOS (default)

	ALC882/885
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  arima		Arima W820Di1
	  targa		Targa T8, MSI-1049 T8
	  asus-a7j	ASUS A7J
	  asus-a7m	ASUS A7M
	  macpro	MacPro support
	  mbp3		Macbook Pro rev3
	  imac24	iMac 24'' with jack detection
	  w2jc		ASUS W2JC
	  auto		auto-config reading BIOS (default)

	ALC883/888
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  acer-aspire	Acer Aspire 9810
	  medion	Medion Laptops
	  medion-md2	Medion MD2
	  targa-dig	Targa/MSI
	  targa-2ch-dig	Targs/MSI with 2-channel
	  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
	  lenovo-101e	Lenovo 101E
	  lenovo-nb0763	Lenovo NB0763
	  lenovo-ms7195-dig Lenovo MS7195
	  haier-w66	Haier W66
	  6stack-hp	HP machines with 6stack (Nettle boards)
	  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
	  6stack-dell	Dell machines with 6stack (Inspiron 530)
	  mitac		Mitac 8252D
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
	  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
	  lenovo	Lenovo 3000 C200
	  dallas	Dallas laptops
	  hp		HP TX1000
	  auto		auto-config reading BIOS (default)

	CMI9880
	  minimal	3-jack in back
	  min_fp	3-jack in back, 2-jack in front
	  full		6-jack in back, 2-jack in front
	  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
	  allout	5-jack in back, 2-jack in front, SPDIF out
	  auto		auto-config reading BIOS (default)

	AD1882
	  3stack	3-stack mode (default)
	  6stack	6-stack mode

	AD1884A / AD1883 / AD1984A / AD1984B
	  desktop	3-stack desktop (default)
	  laptop	laptop with HP jack sensing
	  mobile	mobile devices with HP jack sensing

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
	  dell		Dell T3400

	AD1986A
	  6stack	6-jack, separate surrounds (default)
	  3stack	3-stack, shared surrounds
	  laptop	2-channel only (FSC V2060, Samsung M50)
	  laptop-eapd	2-channel with EAPD (Samsung R65, ASUS A6J)
	  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
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
	  laptop-hpsense    Laptop with HP sense (old model laptop)
	  laptop-micsense   Laptop with Mic sense (old model fujitsu)
	  laptop-hpmicsense Laptop with HP and Mic senses
	  benq		Benq R55E
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

	Conexant 5051
	  laptop	Basic Laptop config (default)
	  hp		HP Spartan laptop

	STAC9200
	  ref		Reference board
	  dell-d21	Dell (unknown)
	  dell-d22	Dell (unknown)
	  dell-d23	Dell (unknown)
	  dell-m21	Dell Inspiron 630m, Dell Inspiron 640m
	  dell-m22	Dell Latitude D620, Dell Latitude D820
	  dell-m23	Dell XPS M1710, Dell Precision M90
	  dell-m24	Dell Latitude 120L
	  dell-m25	Dell Inspiron E1505n
	  dell-m26	Dell Inspiron 1501
	  dell-m27	Dell Inspiron E1705/9400
	  gateway	Gateway laptops with EAPD control

	STAC9205/9254
	  ref		Reference board
	  dell-m42	Dell (unknown)
	  dell-m43	Dell Precision
	  dell-m44	Dell Inspiron

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
	  dell-d81	Dell (unknown)
	  dell-d82	Dell (unknown)
	  dell-m81	Dell (unknown)
	  dell-m82	Dell XPS M1210

	STAC9202/9250/9251
	  ref		Reference board, base config
	  m2-2		Some Gateway MX series laptops
	  m6		Some Gateway NX series laptops
	  pa6		Gateway NX860 series

	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF
	  dell-3stack	Dell Dimension E520
	  dell-bios	Fixes with Dell BIOS setup

	STAC92HD71B*
	  ref		Reference board
	  dell-m4-1	Dell desktops
	  dell-m4-2	Dell desktops

	STAC92HD73*
	  ref		Reference board
	  dell-m6	Dell desktops

	STAC9872
	  vaio		Setup for VAIO FE550G/SZ110
	  vaio-ar Setup for VAIO AR
```

---

### Post by desideratha on 2008-08-08
Hi thanks, I try many options, at the end the one I use and it's working was: 

options snd-hda-intel model=fujitsu  hoever I have a sony vaio,,.?


Thanks for your help...

---

### Post by Crafty Kisses on 2008-08-08
Mark the thread solved.

---

### Post by desideratha on 2008-08-12
Sorry, I really dont know what happened, sound is back on the internal speakers when using headphones?? 

Any ideas, anyone

Thanks

I have a sony vaio vgn-n250

I was using this option
options snd-hda-intel model=fujitsu

---

### Post by desideratha on 2008-08-15
this works

options snd-hda-intel model=basic probe_mask=1

it gives headphones a new set of faders...

(laptop sony vaio vgn-n250)

---

