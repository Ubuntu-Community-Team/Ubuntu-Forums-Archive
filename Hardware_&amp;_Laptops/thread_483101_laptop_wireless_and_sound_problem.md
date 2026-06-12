---
title: "laptop wireless and sound problem"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by Crishu on 2007-06-24
Model: Fujitsu-Siemens Amilo Li 1718
[http://www.fujitsu-siemens.com/home/products/notebooks/amilo_li_1718.html](http://www.fujitsu-siemens.com/home/products/notebooks/amilo_li_1718.html)

lspci -v | less:
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	Memory behind bridge: c0000000-c00fffff
	Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at c0507000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 40000000 [disabled] [size=512K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0504000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0505000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: 66MHz, medium devsel
	I/O ports at 8450 [size=16]
	Memory at c0507400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 82 [Master PriP])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: **ATI Technologies Inc SB450 HDA Audio (rev 01)**
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=0a, subordinate=0c, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 20
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller:** Atheros Communications, Inc. Unknown device 001c (rev 01)**
	Subsystem: Atheros Communications, Inc. Unknown device 3067
	Flags: fast devsel, IRQ 17
	Memory at c0000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

0a:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10c2
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at a000 [size=256]
	Memory at c0200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

lspci -n:
```
00:00.0 0600: 1002:5a31 (rev 01)
00:01.0 0604: 1002:5a3f
00:04.0 0604: 1002:5a36
00:12.0 0101: 1002:4379 (rev 80)
00:13.0 0c03: 1002:4374 (rev 80)
00:13.1 0c03: 1002:4375 (rev 80)
00:13.2 0c03: 1002:4373 (rev 80)
00:14.0 0c05: 1002:4372 (rev 83)
00:14.1 0101: 1002:4376 (rev 80)
**00:14.2 0403: 1002:437b (rev 01)**
00:14.3 0601: 1002:4377 (rev 80)
00:14.4 0604: 1002:4371 (rev 80)
01:05.0 0300: 1002:5a62
**02:00.0 0200: 168c:001c (rev 01)**
0a:07.0 0200: 10ec:8139 (rev 10)

```

that's all i can offer for now .. anything else please ask :)
also i have a couple of buttons that were not recognized(wifi start(figuers), a silent mode and something "i" (donno..didn't use it in windows,maybe browser or info?!)) .. but first things first.
 i myself have done some research but didn't quite get the bugs out of it .. i'll tell u if i regonize them in your responses.
might i add that i am pretty new to ubuntu(but leaning faaast ); just have recently installed a dual-boot on my pc and all is peachy.. made a total switch! ( exept  for when i am in a gaming mood :P ) and now i wanted to see how it handels a laptop,but sadly i had experienced these problems :)
so please help! (and be patient :D )

---

### Post by cobalt01 on 2007-07-09
Hi, 
I got an Amilo li 1718 laptop and aslo can't get the wireless and sound to work. Please help!

Thanks very much!

---

### Post by stchman on 2007-07-09
> **Crishu said:**
> Model: Fujitsu-Siemens Amilo Li 1718
[http://www.fujitsu-siemens.com/home/products/notebooks/amilo_li_1718.html](http://www.fujitsu-siemens.com/home/products/notebooks/amilo_li_1718.html)

lspci -v | less:
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	Memory behind bridge: c0000000-c00fffff
	Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at c0507000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 40000000 [disabled] [size=512K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0504000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0505000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: 66MHz, medium devsel
	I/O ports at 8450 [size=16]
	Memory at c0507400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 82 [Master PriP])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: **ATI Technologies Inc SB450 HDA Audio (rev 01)**
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=0a, subordinate=0c, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10fb
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 20
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller:** Atheros Communications, Inc. Unknown device 001c (rev 01)**
	Subsystem: Atheros Communications, Inc. Unknown device 3067
	Flags: fast devsel, IRQ 17
	Memory at c0000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

0a:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10c2
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at a000 [size=256]
	Memory at c0200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

lspci -n:
```
00:00.0 0600: 1002:5a31 (rev 01)
00:01.0 0604: 1002:5a3f
00:04.0 0604: 1002:5a36
00:12.0 0101: 1002:4379 (rev 80)
00:13.0 0c03: 1002:4374 (rev 80)
00:13.1 0c03: 1002:4375 (rev 80)
00:13.2 0c03: 1002:4373 (rev 80)
00:14.0 0c05: 1002:4372 (rev 83)
00:14.1 0101: 1002:4376 (rev 80)
**00:14.2 0403: 1002:437b (rev 01)**
00:14.3 0601: 1002:4377 (rev 80)
00:14.4 0604: 1002:4371 (rev 80)
01:05.0 0300: 1002:5a62
**02:00.0 0200: 168c:001c (rev 01)**
0a:07.0 0200: 10ec:8139 (rev 10)

```

that's all i can offer for now .. anything else please ask :)
also i have a couple of buttons that were not recognized(wifi start(figuers), a silent mode and something "i" (donno..didn't use it in windows,maybe browser or info?!)) .. but first things first.
 i myself have done some research but didn't quite get the bugs out of it .. i'll tell u if i regonize them in your responses.
might i add that i am pretty new to ubuntu(but leaning faaast ); just have recently installed a dual-boot on my pc and all is peachy.. made a total switch! ( exept  for when i am in a gaming mood :P ) and now i wanted to see how it handels a laptop,but sadly i had experienced these problems :)
so please help! (and be patient :D )

This assumes you are running Feisty.

My laptop has the same hardware.  What version of Ubuntu are you running?  Feisty has good support for Atheros card out of the box.  First thing is to see if teh Atheros HAL driver is enabled.  If it is not then enable it.  If it is then you will ahve to use the madwifi drivers.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Disregard the network manager since you are running Feisty.

Sound, try this:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

Look under the SB450 stuff.

I hope this helps.

---

### Post by cobalt01 on 2007-07-10
Hi stchman,
thanks very much for your help.
By the way, your site is great, a lot of very usefull stuff!

I tried both your tips and followed the instructions very carefully but could not get neither the wifi nor the soundcard to work. After I went through your instructions and installed madwifi-0.9.3.1 (which worked without a hitch) I rebooted.
Then I tried wiconfig with the result:

lo	no wireless extensions.
eth0	no wireless extensions.

Also when I open Systems > Administrations > Network
There is no wireless connection visible…

Then I thought it might be due to the wireless hotkey on the laptop and I followed the instructions to activate acerhk according to this site:
[http://damagedspline.blogspot.com/2007/03/fsc-amilo-a1650g-ubuntu-fiesty-32bit.html](http://damagedspline.blogspot.com/2007/03/fsc-amilo-a1650g-ubuntu-fiesty-32bit.html)

but still no luck…anything else I can try? 

Yes I'm running feisty with the latest updates.

---

### Post by iansyngin on 2007-07-10
also running  a Fujitsu model laptop with no sound.
Have tried most of the tips on various threads over the last few months but still don't have sound working. One thing that i should mention though. Just before Ubuntu splash screen loads, a BIOS Bug message quickly appears then disappears. I can get these details if anyone wants more info. Sound is working fine on XP as im dual booting so doubt that this is the cause

---

### Post by cobalt01 on 2007-07-11
I also run XP as a second OS on dual boot and there everything, sound and wireless works fine. I would like to get read of the XP install but first I have to find a way to get wireless and sound working in ubuntu :(

---

### Post by McScruff on 2007-07-12
i too have an amilo 1718

i never looked into the sound problem but i do understand the wifi one.

A) The wifi card uses a new HAL module that isnt compatible with madwifi, so ubuntu knows its an atheros card but can't use it.  I also tried many drivers with ndiswrapper and never got any of them working, device was found but it threw up errors in dmesg.

---

### Post by cobalt01 on 2007-07-13
Thanks McScruff for confirming the problem with the HAL module on the Atheros wifi.

 I thought I'll give it a shot and try out some of the win drivers with the ndiswrapper. If I do so, do I have to uninstall madwifi first and if so how do I do that? Or can I install ndiswrapper directly over madwifi?

---

### Post by McScruff on 2007-07-13
should be able to use it over the top, or you can blacklist the ath_pci module

---

### Post by stchman on 2007-07-13
> **cobalt01 said:**
> Hi stchman,
thanks very much for your help.
By the way, your site is great, a lot of very usefull stuff!

I tried both your tips and followed the instructions very carefully but could not get neither the wifi nor the soundcard to work. After I went through your instructions and installed madwifi-0.9.3.1 (which worked without a hitch) I rebooted.
Then I tried wiconfig with the result:

lo	no wireless extensions.
eth0	no wireless extensions.

Also when I open Systems > Administrations > Network
There is no wireless connection visible…

Then I thought it might be due to the wireless hotkey on the laptop and I followed the instructions to activate acerhk according to this site:
[http://damagedspline.blogspot.com/2007/03/fsc-amilo-a1650g-ubuntu-fiesty-32bit.html](http://damagedspline.blogspot.com/2007/03/fsc-amilo-a1650g-ubuntu-fiesty-32bit.html)

but still no luck…anything else I can try? 

Yes I'm running feisty with the latest updates.

For Atheros cards you will have ath0 not eth0.

Did you try enabling the restricted drivers for Atheros?  They work very well.

---

### Post by McScruff on 2007-07-14
> **stchman said:**
> For Atheros cards you will have ath0 not eth0.

Did you try enabling the restricted drivers for Atheros?  They work very well.


they work very well if the HAL is supported...

I haved solved my wifi (with ndiswrapper) and sound issues, i will post in a few hours after work and after harry potter (o i cant wait to go see it!!!!!!!)

all the links are on these forums but cant remember what i searched

---

### Post by Crishu on 2007-11-01
> **McScruff said:**
> they work very well if the HAL is supported...

I haved solved my wifi (with ndiswrapper) and sound issues, i will post in a few hours after work and after harry potter (o i cant wait to go see it!!!!!!!)

all the links are on these forums but cant remember what i searched

If you wold be so kind to share with us! :)
(btw .. the movie was ok i guess )

    Long time .. no  post, if i may say, Looking back at that time i managed to get the sound working :D but gave up on the wi-fi.
I accepted the situation at hoped that the next ubuntu realese would cover my problem.
(..time passing..)
So finally i've uprgaded just recently to 7.10. I am happy to see that now my onboard ATI X200M can handle 3D acceleration! :D But still no luck with the wi-fi. :( 
When i'll feel up to it i'll try to digg up some more info, maybe in these months some progres was made somewhere! :P

---

