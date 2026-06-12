---
title: "Sound problem with D630 in Gutsy"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by cnshzj007 on 2007-07-06
No sound with Dell D630 in Gutsy. More Information as below.


lspci -v


```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f9
        Flags: fast devsel, IRQ 21
        Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

lshw
```
*-multimedia UNCLAIMED
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress cap_list
             configuration: latency=0

```


 lspci -nv
```
00:00.0 0600: 8086:2a00 (rev 0c)
        Subsystem: 1028:01f9
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA])
        Subsystem: 1028:01f9
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at efe8 [size=8]
        Capabilities: <access denied>

00:02.1 0380: 8086:2a03 (rev 0c)
        Subsystem: 1028:01f9
        Flags: bus master, fast devsel, latency 0
        Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 0c03: 8086:2834 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f20 [size=32]

00:1a.1 0c03: 8086:2835 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f00 [size=32]

00:1a.7 0c03: 8086:283a (rev 02) (prog-if 20 [EHCI])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 0403: 8086:284b (rev 02)
        Subsystem: 1028:01f9
        Flags: fast devsel, IRQ 20
        Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 0604: 8086:283f (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: <access denied>

00:1c.1 0604: 8086:2841 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: fe800000-fe8fffff
        Capabilities: <access denied>

00:1c.5 0604: 8086:2849 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
        Memory behind bridge: fe700000-fe7fffff
        Capabilities: <access denied>

00:1d.0 0c03: 8086:2830 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f80 [size=32]

00:1d.1 0c03: 8086:2831 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f60 [size=32]

00:1d.2 0c03: 8086:2832 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f40 [size=32]

00:1d.7 0c03: 8086:2836 (rev 02) (prog-if 20 [EHCI])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 0604: 8086:2448 (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: fe600000-fe6fffff
        Prefetchable memory behind bridge: 0000000070000000-0000000073ffffff
        Capabilities: <access denied>

00:1f.0 0601: 8086:2815 (rev 02)
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 0101: 8086:2850 (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]

00:1f.2 0101: 8086:2828 (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: 1028:01f9
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=16]
        I/O ports at eff0 [size=16]
        Capabilities: <access denied>

00:1f.3 0c05: 8086:283e (rev 02)
        Subsystem: 1028:01f9
        Flags: medium devsel, IRQ 10
        Memory at fe9fbf00 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]

03:01.0 0607: 1217:7135 (rev 21)
        Subsystem: 1028:01f9
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 18
        Memory at fe600000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 70000000-73fff000 (prefetchable)
        Memory window 1: 74000000-77fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

03:01.4 0c00: 1217:00f7 (rev 02) (prog-if 10 [OHCI])
        Subsystem: 1028:01f9
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at fe6ff000 (32-bit, non-prefetchable) [size=4K]
        Memory at fe6fe800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

09:00.0 0200: 14e4:1673 (rev 02)
        Subsystem: 1028:01f9
        Flags: bus master, fast devsel, latency 0, IRQ 220
        Memory at fe7f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

0c:00.0 0280: 8086:4222 (rev 02)
        Subsystem: 8086:1022
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fe8ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```

---

### Post by bsawler on 2007-07-07
see this for a start.  hopefully it should help. 

[http://ubuntuforums.org/showthread.php?p=2974858#post2974858](http://ubuntuforums.org/showthread.php?p=2974858#post2974858)

---

### Post by cnshzj007 on 2007-07-07
Thanx u ~!
U r a cool GUY!

---

### Post by cnshzj007 on 2007-07-07
D630 is not support by the latest ALSA driver.

---

### Post by cnshzj007 on 2007-07-07
There is no list in the ALSA-Configuration.txt about D630.
```
Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
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
	  auto		auto-config reading BIOS (default)

	CMI9880
	  minimal	3-jack in back
	  min_fp	3-jack in back, 2-jack in front
	  full		6-jack in back, 2-jack in front
	  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
	  allout	5-jack in back, 2-jack in front, SPDIF out
	  auto		auto-config reading BIOS (default)

	AD1981
	  basic		3-jack (default)
	  hp		HP nx6320
	  thinkpad	Lenovo Thinkpad T60/X60/Z60
	  toshiba	Toshiba U205

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
	  macmini	Intel Mac Mini
	  macbook	Intel Mac Book
	  macbook-pro-v1 Intel Mac Book Pro 1st generation
	  macbook-pro	Intel Mac Book Pro 2nd generation
	  imac-intel	Intel iMac

	STAC9202/9250/9251
	  ref		Reference board, base config
	  m2-2		Some Gateway MX series laptops
	  m6		Some Gateway NX series laptops

	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF

	STAC9872
	  vaio		Setup for VAIO FE550G/SZ110
	  vaio-ar Setup for VAIO AR

    The model name "genric" is treated as a special case.  When this
    model is given, the driver uses the generic codec parser without
    "codec-patch".  It's sometimes good for testing and debugging.

    If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").

    Note 2: If you get click noises on output, try the module option
	    position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
	    register value without FIFO size correction as the current
	    DMA pointer.  position_fix=2 will make the driver to use
	    the position buffer instead of reading SD_LPIB register.
	    (Usually SD_LPLIB register is more accurate than the
	    position buffer.)

    NB: If you get many "azx_get_response timeout" messages at
    loading, it's likely a problem of interrupts (e.g. ACPI irq
    routing).  Try to boot with options like "pci=noacpi".  Also, you
    can try "single_cmd=1" module option.  This will switch the
    communication method between HDA controller and codecs to the
    single immediate commands instead of CORB/RIRB.  Basically, the
    single command mode is provided only for BIOS, and you won't get
    unsolicited events, too.  But, at least, this works independently
    from the irq.  Remember this is a last resort, and should be
    avoided as much as possible...
    
    The power-management is supported.

```

---

### Post by bsawler on 2007-07-07
what is the output from:

```
cat /proc/asound/card0/codec\#*
```

Look for the codec (near the top of the output) and search for this in the ALSA-Conf...txt file.

---

### Post by warreng on 2007-07-07
I have the same problem (with a Dell D830). If I cat /proc/asound/cards it reports no sound cards installed. However, sound works OK in Feisty.

> cat /proc/asound/cards
--- no soundcards ---

I believe the card is a STAC9205, which according to the ALSA docs should work with snd-hda-intel / model = 3stack. However, configuring this in alsabase does nothing.

If I run alsaconf, it sees the card and claims to configure it, but it still doesn't work. There's a kernel message on loading snd-hda-intel, as follows:

>> ALSA /usr/src/alsa/alsa-driver-1.0.14rc4/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1020: hda-intel: no codecs initialized

Any help gratefully received :-)

On the plus side (and a bit off topic) Gutsy (32 bit) has solved my other issues with Feisty including lock-up on opengl apps. Beryl / compiz both work really well. 64 bit was similar but wireless didn't work.

---

### Post by cnshzj007 on 2007-07-07
[B]Yes!
no soundcards
Bad luck!
I have done alsaconf.
Then no sound!
Any Help better than none!
Looking for.[/B]

---

### Post by cnshzj007 on 2007-07-08
This url is to solve the problem by compiling the hda_intel driver to the kernal. But I dont know how to compile the hda_intel driver to the kernal.
Any help than none.
[http://www.gossamer-threads.com/lists/linux/kernel/783754+D630&hl=sv&ct=clnk&cd=18&gl=se]("http://www.gossamer-threads.com/lists/linux/kernel/783754+D630&hl=sv&ct=clnk&cd=18&gl=se")

---

### Post by cnshzj007 on 2007-07-16
UP!
any help?
I can not bear the silent world of the laptop D630 with Gusty.

---

### Post by cnshzj007 on 2007-07-20
UPUPUP&#65281;
What drives me back to the XP?
No Sound.
Crazy.

---

### Post by cnshzj007 on 2007-07-31
UPUPUP
Too long to bear the life without sound in my laptop D630.
Any help?

---

### Post by tonyric on 2007-08-02
Folks, remember that the 630's and 830's were released after Feisty. Gutsy (which is just about to enter BETA testing and still has many problems) will fix these issues. Patience folks. If you cannot wait, then download the latest Xorg 7.3 and kernel and alsa code and compile them yourself. lol This is how the community works. Showing frustration only causes more frustration on yoru part and causes an unwillingness in others to help. There are fixes to the sound problem in the forums, just search for it. if you don't find it with searching for the D630, try searching for the D830.

Tony

---

### Post by cnshzj007 on 2007-08-02
> **tonyric said:**
> Folks, remember that the 630's and 830's were released after Feisty. Gutsy (which is just about to enter BETA testing and still has many problems) will fix these issues. Patience folks. If you cannot wait, then download the latest Xorg 7.3 and kernel and alsa code and compile them yourself. lol This is how the community works. Showing frustration only causes more frustration on yoru part and causes an unwillingness in others to help. There are fixes to the sound problem in the forums, just search for it. if you don't find it with searching for the D630, try searching for the D830.

Tony

Thanks a lot.
U C I have tried a lot showed above to solve the problem but none works fine.
I know I am crazy.I know I love the ubuntu so much.I know I love the music so much.
And above all I must make it clear that I respect all coders and contributors.

---

### Post by fredj on 2007-08-02
Well ok all this is very interesting but it gets us nowhere. Can you open a terminal and type
sudo lshw -class sound. Then post the output from that here. Also in a terminal go to the 
/proc/asound directory and type ls. Post the output from that here.

---

### Post by Gremlinzzz on 2007-08-03
Thanks Walkerk. Your instructions worked flawlessly and ended weeks of frustration trying to get sound to work on my new laptop. Much appreciated. this was a reply from a member called stOnes.He upgrade his kernel seems to me the feisty kernel doesn't work well with laptops.I upgraded mine using the manual instructions and it works great.im using a desktop.you could give it a shot .
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by cnshzj007 on 2007-08-05
> **fredj said:**
> Well ok all this is very interesting but it gets us nowhere. Can you open a terminal and type
sudo lshw -class sound. Then post the output from that here. Also in a terminal go to the 
/proc/asound directory and type ls. Post the output from that here.

bond007@ubuntu007:~$ sudo lshw -class sound
[sudo] password for bond007:
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
bond007@ubuntu007:~$ 


bond007@ubuntu007:/proc/asound$ ls
cards  devices  modules  oss  pcm  seq  timers  version

---

### Post by cnshzj007 on 2007-08-05
Core is updated to 2.6.22-9-generic.
Bad luck. No sound at all.
OK. 
Please
God
Help.

---

### Post by o3rat on 2007-08-05
Same problem here, no sound. I'm running 2.6.22-9-generic. As soon as I got the wifi the work sound get detected. 

Any ideas?

---

### Post by cnshzj007 on 2007-08-06
> **o3rat said:**
> Same problem here, no sound. I'm running 2.6.22-9-generic. As soon as I got the wifi the work sound get detected. 

Any ideas?

Then how to get the wifi work?
b

---

### Post by rybley on 2007-08-06
After a few weeks of no sound with the d630 and the 2.6.22 kernel, I finally found this solution, which worked for me.  I must warn you that I am kind of new to linux and can make no guarantees that this solution will work or that it will not hurt your system.  I found it on [http://onemansjourneyintolinux.blogspot.com/2007/06/d630-update.html](http://onemansjourneyintolinux.blogspot.com/2007/06/d630-update.html), so thanks to commenter Mike, who is an angel.
Here goes:
1. Get the latest alsa drivers from Georgia Tech's website
> wget [http://www.gtlib.gatech.edu/pub/suse/projects/alsa/snapshot/driver/alsa-driver-hg20070804.tar.bz2](http://www.gtlib.gatech.edu/pub/suse/projects/alsa/snapshot/driver/alsa-driver-hg20070804.tar.bz2)

2. extract it
3. change directory to the directory with the extracted files
4. configure with > ./configure --with-cards-hda-intel 
5. > make
6. > sudo make install
7. reboot
I hope it works as well for you guys as it did for me.  Good luck.

---

### Post by cnshzj007 on 2007-08-06
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

---

### Post by cnshzj007 on 2007-08-06
> **rybley said:**
> After a few weeks of no sound with the d630 and the 2.6.22 kernel, I finally found this solution, which worked for me.  I must warn you that I am kind of new to linux and can make no guarantees that this solution will work or that it will not hurt your system.  I found it on [http://onemansjourneyintolinux.blogspot.com/2007/06/d630-update.html](http://onemansjourneyintolinux.blogspot.com/2007/06/d630-update.html), so thanks to commenter Mike, who is an angel.
Here goes:
1. Get the latest alsa drivers from Georgia Tech's website


2. extract it
3. change directory to the directory with the extracted files
4. configure with  
5. 
6. 
7. reboot
I hope it works as well for you guys as it did for me.  Good luck.

Thank U very very much!

How to solve that below?

cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

---

### Post by cnshzj007 on 2007-08-06
It works fine!
Thanks God@!
Thanks above all!
Here is the deb that may be helpfull to those who met the same problem.
SORRY, the deb package is too big to upload >18MB

---

### Post by Diablohtr on 2007-08-16
Thanks for the help! Works great for my D830http://ubuntuforums.org/images/smilies/guitar.gif

---

### Post by ntaylor0909 on 2007-10-10
I tried your solution, but I get the following error when I run the ./configure command:

nathan@nathan-laptop:~/alsa-driver-hg20070804$ ./configure --with-cards-hda-intel
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
nathan@nathan-laptop:~/alsa-driver-hg20070804$ 


Help?

---

### Post by tturrisi on 2007-10-10
Very easy to get sound in the D630 & D840 Lattitudes.
See my guide here:
[http://members.cox.net/tonyt/d830](http://members.cox.net/tonyt/d830)

Remember, if building alsa from source to FIRST completely remove the existing alsa-base using synaptic.

---

### Post by ntaylor0909 on 2007-10-11
I get the same error while following your instructions:

nathan@nathan-laptop:/usr/src/alsa-driver-hg20070922$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
nathan@nathan-laptop:/usr/src/alsa-driver-hg20070922$

---

### Post by tturrisi on 2007-10-11
> **ntaylor0909 said:**
> I get the same error while following your instructions:

nathan@nathan-laptop:/usr/src/alsa-driver-hg20070922$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
nathan@nathan-laptop:/usr/src/alsa-driver-hg20070922$

apt-get install build-essential

---

### Post by ntaylor0909 on 2007-10-13
Thanks, that worked to get me past that first issue. How did you know to have me use that command. Just curious. I am trying to learn some of this stuff and was curious. ALso I was able to follow the instructions all the way to the run alsaconf command. I get the following error:
nathan@nathan-laptop:/$ alsaconf
bash: alsaconf: command not found

Thanks again for all of your help. The community around Linux and ubuntu is just amazing. It is so cool that you can ask a question and it gets answered so quickly and expertly. Thanks.:)

---

### Post by tturrisi on 2007-10-15
> **ntaylor0909 said:**
> Thanks, that worked to get me past that first issue. How did you know to have me use that command. Just curious. I am trying to learn some of this stuff and was curious. ALso I was able to follow the instructions all the way to the run alsaconf command. I get the following error:
nathan@nathan-laptop:/$ alsaconf
bash: alsaconf: command not found

Thanks again for all of your help. The community around Linux and ubuntu is just amazing. It is so cool that you can ask a question and it gets answered so quickly and expertly. Thanks.:)

build-essential:
required for building from source

alsaconf:  [http://members.cox.net/tonyt/d830/#audio](http://members.cox.net/tonyt/d830/#audio)
apt-get install alsa-utils

---

### Post by ntaylor0909 on 2007-10-15
Thanks again for your help. Here is what I get when I run that command:

nathan@nathan-laptop:~$ sudo apt-get install alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nathan@nathan-laptop:~$ alsaconf
bash: alsaconf: command not found
nathan@nathan-laptop:~$

---

### Post by tturrisi on 2007-10-15
sudo alsaconf

---

### Post by ntaylor0909 on 2007-10-15
I tried that and I get the same error. 

nathan@nathan-laptop:~$ sudo alsaconf
[sudo] password for nathan:
sudo: alsaconf: command not found
nathan@nathan-laptop:~$ 

:confused:

---

### Post by tturrisi on 2007-10-15
try
sudo /usr/sbin/alsaconf
if no joy do
whereis alsaconf
then run the path

---

### Post by ntaylor0909 on 2007-10-15
Thanks again for all of your help. I am learning a lot from this experience. Are there some options I need to give whereis when I run it? I don't quite understand the response from the comand.

 nathan@nathan-laptop:~$ sudo /usr/sbin/alsaconf
[sudo] password for nathan:
sudo: /usr/sbin/alsaconf: command not found
nathan@nathan-laptop:~$ whereis alsaconf
alsaconf:
nathan@nathan-laptop:~$

---

### Post by tturrisi on 2007-10-16
alsaconf is in either /usr/bin or in your home dir somewhere.
you can also try:
locate alsaconf
or
find alsaconf

as well as:
man whereis
man locate
man find

---

### Post by ntaylor0909 on 2007-10-18
I was never able to get that to work. It never found alsaconf. 

But, I did finally get the sound working. On the ubuntu Wiki, they have a solution:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Woohoo. Sound. On My D630 with Gutsy installed, that was my only hurdle. I even got my d-port docking station to work. 

Thanks again for all of your help.:)

---

### Post by cnshzj007 on 2007-11-08
Sound driver

[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)

./configure --with-cards-hda-intel;make;sudo make install;

---

