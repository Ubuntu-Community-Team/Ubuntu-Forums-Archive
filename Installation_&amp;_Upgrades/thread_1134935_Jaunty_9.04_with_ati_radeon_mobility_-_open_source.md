---
title: "Jaunty 9.04 with ati radeon mobility - open source drivers vs. fglrx in 8.10"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by alonso on 2009-04-24
**Please post you experiences with mobility radeon and 9.04 open source ati drivers!**

Since there seems to be a lot of discussion on the fact that fglrx drivers (xorg-driver-fglrx) are no longer supported in 9.04, I am (and many more are) hesitant on installing jaunty on my laptop with the open source ones (xserver-xorg-video-radeon and/or xserver-xorg-video-ati). I have ati mobility radeon x600 (R300 series). 

$ lspci | grep Radeon
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon MobilityX600]

I tried the live cd and it was mostly working but I got some screen corruption and scrolling speed seemed worse.

I am interested at least on these:

The model of your video card.
The performance of : 2d (e.g., scrolling), 3d (glxgears), xv full screen (which resolution) video, xv windowed video? Especially compared to 8.10 using fglrx.
Did you have to tweak your xorg.conf?

Thank you very muchos!

---

### Post by eggplant37 on 2009-04-24
I'm not at all happy; in fact, I'm raging like hell. I'll keep it professional and let's see if we can get the rage demon calmed down here. 

I've a Dell Inspiron 1501 laptop with embedded ATI Technologies Inc RS482 [Radeon Xpress 200M]. Here's the rundown on my gear:

```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
	Memory behind bridge: c0200000-c02fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8438 [size=8]
	I/O ports at 8454 [size=4]
	I/O ports at 8430 [size=8]
	I/O ports at 8450 [size=4]
	I/O ports at 8400 [size=16]
	Memory at c0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at c0008000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0009000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0004400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
	Subsystem: Dell Device 01f5
	Flags: 66MHz, medium devsel
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8420 [size=16]
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Dell Device 01f5
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
	Memory behind bridge: c0300000-c03fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
	Subsystem: Dell Device 01f5
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Dell Device 0007
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: wl, ssb

08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01f5
	Flags: bus master, fast devsel, latency 64, IRQ 21
	Memory at c0300000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: Dell Device 01f5
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at c0302800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
	Subsystem: Dell Device 01f5
	Flags: bus master, medium devsel, latency 0, IRQ 9
	Memory at c0302c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: ricoh_mmc

```

Here's my xorg.conf:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section	"Module"
	Load "glx"
	Load "dri"
EndSection

#Section "Device"
#	Identifier  "Default Device"
#	Driver      "vesa"
#EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver	"ati"
	BusID       "PCI:1:5:0"
	Option	"XAANoOffscreenPixmaps"
#	Option	"AccelMethod"	"XAA"
	Option	"AccelMethod"	"EXA"
	Option 	"EnablePageFlip" "true"
	Option	"TripleBuffer"	"true"
	Option	"ColorTiling" "1"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group "video"
	Mode 066
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

Everything was fine up until last night when I rebooted after completing the upgrade from 8.10 to 9.04. 

I hop on World of Warcraft. Mind you, since the 9.3 release of fglrx, I wasn't getting any real performance out of the chip. Average of 10 fps was best I could get in Warcraft, with zones like Dalaran or Argent Stand in Gundrak down more around 5 fps. 

I've a dwarf bank toon that I keep in Darnassus to mind my auctions and cash since Darnassus usually averages 10-15 fps due to the low population and easy to draw graphics. Now, after the upgrade, this one's getting graphics lag at a single frame per second or less. I've tried tweaking and jacking settings around until midnight last night and then another hour and a half today.

Can someone please tell me WTF is up here? Am I going to have to back up a bunch of data and reformat and reload 8.10 to fix this idiocy? 3D graphics was working just fine before the 9.04 upgrade and I cannot think of a single reason why it shouldn't continue to do so.  Ideas? Explanations?

There's a thread amongst the forums that recommends recompiling mesa, and even more about how fglrx drivers will drop support for my chip, but whether there's a valid fix or any work done to that end is a totally different question.

I'm lost and very frustrated. Help.

P.S. 12:32 p.m. UTC -0400 24/04/09:

Looking more for possible fixes on the issue, this bug appears to be the exact problem that needs to be addressed to save some face here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569)

And this describes fixes that were done somewhere along the way and mentioned in the link above:

[http://www.nabble.com/R300-regression-td23108996.html](http://www.nabble.com/R300-regression-td23108996.html)

P.P.S. 8:53 a.m.:

Bump for great justice.

---

### Post by CodeRage on 2009-04-27
I have exactly the same set up (Dell Inspiron 1501 with same ATI card, about 2.5 to 3 years old). Unfortunately for those of us that cannot afford to just run out and get a snarling new computer, we're stuck with just living on the outskirts of technology and software. 

I too just did the upgrade to Jaunty 9.04 today and found my fglrx won't work. I got the prompt before the upgrade about the drivers, so before I upgraded, I removed my fglrx and then went to do the upgrade (which still told me about fglrx not working with 9.04). Lo and behold there is no driver working for it, and i'm not exactly savvy enough with linux to do manual installs. 

Oh well. I can deal with what I can deal with for a while. If our vid card can't be supported in jaunty, then I think i'll revert back to at least intrepid if not hardy.

CodeRage

---

### Post by Dan42 on 2009-04-29
I have a Radeon Xpress 200 (RS480) and when I upgraded to **8.10** I found that it was no longer supported in fglrx. I'm not really sure why this is only hitting you guys now, maybe it was just a matter of time until incompatibility caught up with you :-/

I'm not keen on upgrading to 9.04 if I have to go through this whole rigmarole again, but at least on 8.10 I managed to get my card back to some level of performance using the ati driver (after much messing around). I don't use any 3D apps though, so maybe my "some level of performance" won't mean much to you. IIRC, among the myriad of configuration tweaks I tried, the key was specifying the resolutions supported by my monitor... but maybe it was something else that did the trick. Anyway, just posting this in case it's of use to someone. Keep in mind that this is using the "ati" driver on 8.10

my xorg.cong
```

Section "Files"
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Monitor"
	Identifier	"N91S"
	Option		"DPMS"
	Horizsync	30-80
	Vertrefresh	60-75
	Displaysize	375	302
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Monitor		"N91S"
	DefaultDepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Busid		"PCI:1:5:0"
	Screen	0
	Driver		"ati"
EndSection

```

Running glxgears gives me
> 4355 frames in 5.0 seconds = 870.883 FPS
4394 frames in 5.0 seconds = 878.662 FPS
4392 frames in 5.0 seconds = 878.292 FPS
4384 frames in 5.0 seconds = 876.710 FPS


EDIT:

But running glxgears -fullscreen gives me
> 544 frames in 5.0 seconds = 108.751 FPS
542 frames in 5.0 seconds = 108.273 FPS
542 frames in 5.0 seconds = 108.294 FPS
542 frames in 5.0 seconds = 108.275 FPS

So I guess my 3D performance is utter crap after all. :-(

---

### Post by StuartN on 2009-04-29
> **CodeRage said:**
> I too just did the upgrade to Jaunty 9.04 today and found my fglrx won't work. I got the prompt before the upgrade about the drivers, so before I upgraded, I removed my fglrx and then went to do the upgrade (which still told me about fglrx not working with 9.04). Lo and behold there is no driver working for it, and i'm not exactly savvy enough with linux to do manual installs.

I have the Dell Inspiron 1501, although I didn't upgrade. The Radeon Xpress 200M does work okay when running the Ubuntu 9.04 Live CD and everything is detected and installed faultlessly. The "okay" performance of the open source driver under 9.04 is well below the fglrx driver under 8.10 - I get just 320 fps in glxgears compared to 2,200 under 8.10, so one seventh of the speed.

The following link may help if you upgraded (rather then a clean install) and corrects some hangovers when a previous fglrx installation interferes with a newly-installed open source driver: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by chubby on 2009-05-02
Well it took me sooo long to work out how to get my tv out working on the card below in Hardy but eventually I did.
I upgraded to Jaunty and then read the info on the ATI website.
No TV out anymore. And the computer works just like it did before the upgrade so I am considering reloading Hardy as my main use for the computer is watching movies on the TV. Problem is I cannot remember how I got tv out working in the first place... 


01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]

---

### Post by at78rpm on 2009-05-04
I too have a Radeon X600, this one on a ThinkPad Z60m.  I keep telling friends that the only thing keeping Ubuntu from wider acceptance with the Windows world is that it absolutely blows in the video card department.  I'm running Intrepid, and have had my share of problems, some of which I researched on reliable Ubuntu sites, applied recommended fixes, and had to revert to an earlier Linux kernel to get my screen back.  Hoo boy.  

No way will I "upgrade" to Jaunty.  And this is especially sad because one of the main reasons I recommend Ubuntu to people is that it, and its variants like Xubuntu, can be used on older computers to make them run like new.  No longer, it seems.  My 2GHz chip, my 2GB RAM, my x600 are all terribly obsolete.  Except that it works just fine for me, and I see no reason to get the latest and greatest.  However, if Jaunty promises workable TV out, then I'd be interested!

---

### Post by P Minix on 2009-05-05
So it seems I'm in the same sinking boat ith the rest of you guys.

I have an older Dell (ATI RV370 5B60 [RADEON X300], with a clean xorg.conf) that was running 8.10 fine.  The 9.04 upgrade was run. Now no GDM.  The user isn't a CLI junkie, so any ideas on how to do a painless revert back to 8.10.  

I'm guessing that nifty upgrade manager doesn't have a nice command line revert mode?  I would really like t avoid the reconfiguraion process.

---

### Post by autra on 2009-05-05
I run a HP nc8430 with a ati radeon mobility X1600.
I use the open source driver (as I have no choice). This gives me better performance with glxgears (*10 !!!!)
However, I can't use graphic effects.

---

### Post by Mark Phelps on 2009-05-05
> **P Minix said:**
> So it seems I'm in the same sinking boat ith the rest of you guys.

I have an older Dell (ATI RV370 5B60 [RADEON X300], with a clean xorg.conf) that was running 8.10 fine.  The 9.04 upgrade was run. Now no GDM.  The user isn't a CLI junkie, so any ideas on how to do a painless revert back to 8.10.  

I'm guessing that nifty upgrade manager doesn't have a nice command line revert mode?  I would really like t avoid the reconfiguraion process.
There is no simple way to "revert back" to a prior Ubuntu version.  You have to save off what you can and reinstall.

However, you should be able to use the open source driver.  Check out the link below for details:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by P Minix on 2009-05-06
Reverting was a forlorn hope.  It was a dig at the upgrade manager that didn't do a check for known hardware problems. 

The painful part isn't the data, thats all backed up.  Its the application reconfiguration, etc.  Had the process not looked so painless I would have imaged the disk first.

---

### Post by Guitar John on 2009-05-06
```
lspci
```

gives me this

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

```

This is on a Dell D610 laptop.  I'm not a gamer and I can take or leave the desktop effects.  If I upgrade and the card is not supported, does it default to the integrated Intel Graphics Controller on the motherboard?

---

### Post by rainwalker on 2009-05-06
I'm not sure how much use this would be to anyone here, but I'm on an old Dell Inspiron 8600 using the open-source ATI drivers and everything works almost perfectly (one or two little exceptions here and there)
> VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

---

### Post by MBybee on 2009-05-11
I'm running the ATI Radeon X1300 Mobility card on an Acer Aspire 5100.

With Ubuntu 8 and the default proprietary ATI driver, performance was quite decent. Not stunning, but it's not that great a card even under the best conditions.

I did a clean install of Ubuntu 9.04 and the default open source driver functions reasonably well. It is slow for the most part, but something I can live with for 2D.

The 3D performance is terrible, however, and if the machine is suspended the screen is horribly garbled on resume.

I attempted to install the 9.4 ATI driver manually, but it did not recognize my video card and exited safely (so no harm done).

I would not recommend going to Ubuntu 9.04 on this laptop at this time - the overall performance is noticeably worse (probably due to the video driver) and there are really no stability issues with 8.x that I ran into.

In my case, I don't think I'll revert quite yet. I will give it a month or so and see if there are any driver updates.

---

### Post by Dan42 on 2009-05-15
It looks like someone _[here](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569)_ managed to fix this problem using the _[radeon-rewrite](https://launchpad.net/~xorg-edgers/+archive/radeon)_ driver, but my xorg-fu is not strong enough to figure out how to use & configure this :-(

---

### Post by MBybee on 2009-05-23
> **Dan42 said:**
> It looks like someone _[here](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569)_ managed to fix this problem using the _[radeon-rewrite](https://launchpad.net/~xorg-edgers/+archive/radeon)_ driver, but my xorg-fu is not strong enough to figure out how to use & configure this :-(

Thanks for the link!
I installed these drivers, and it worked flawlessly (ATI Radeon X1300 Mobility)

GLX Gears on standard driver

1171 frames in 5.0 seconds = 234.141 FPS
1177 frames in 5.0 seconds = 235.230 FPS
1152 frames in 5.0 seconds = 230.325 FPS
1137 frames in 5.0 seconds = 227.398 FPS
1141 frames in 5.0 seconds = 228.104 FPS
1159 frames in 5.0 seconds = 231.751 FPS
1131 frames in 5.0 seconds = 226.132 FPS

Radeon-Rewrite driver
4335 frames in 5.0 seconds = 866.891 FPS
4207 frames in 5.0 seconds = 841.207 FPS
4237 frames in 5.0 seconds = 847.233 FPS
4316 frames in 5.0 seconds = 863.157 FPS
4407 frames in 5.0 seconds = 881.325 FPS
4404 frames in 5.0 seconds = 880.613 FPS
4425 frames in 5.0 seconds = 884.852 FPS
4313 frames in 5.0 seconds = 862.413 FPS

---

### Post by night-wing on 2009-05-31
Thanks very much!!!

This speeds up my framerates to 1400 fps and makes the jaunty ati problem much smaller :o

---

### Post by ikus060 on 2009-06-01
Hi All,

I've install radeon-rewrite and it's doesn't fix the performance issue I have. Since I upgrade to Jaunty, it's seam that any graphics/video/display operation take mush mush more cpu. As an example, If I move a windows alots or if I change the content of a Windows rapidly I notice a deterioration of the performance.

I know since Jaunty there is many change so it's can be either the radeon driver, the X.org, the Windows Manager and event the kernel scheduler.

I wanna know if you experience this kind of problem. A good test for me is to start a music and stress the display by moving windows of executing gtkperf, etc.

In Hardy, doing the same operation doesn't have any noticable impact on the audio output.

Notes: my video card is a Radeon X300 (M22) and my laptop is a ThinkPad T43

Thanks for any info.

---

### Post by ales on 2009-06-05
> **MBybee said:**
> Thanks for the link!
I installed these drivers, and it worked flawlessly (ATI Radeon X1300 Mobility)

GLX Gears on standard driver

1171 frames in 5.0 seconds = 234.141 FPS
1177 frames in 5.0 seconds = 235.230 FPS
1152 frames in 5.0 seconds = 230.325 FPS
1137 frames in 5.0 seconds = 227.398 FPS
1141 frames in 5.0 seconds = 228.104 FPS
1159 frames in 5.0 seconds = 231.751 FPS
1131 frames in 5.0 seconds = 226.132 FPS

Radeon-Rewrite driver
4335 frames in 5.0 seconds = 866.891 FPS
4207 frames in 5.0 seconds = 841.207 FPS
4237 frames in 5.0 seconds = 847.233 FPS
4316 frames in 5.0 seconds = 863.157 FPS
4407 frames in 5.0 seconds = 881.325 FPS
4404 frames in 5.0 seconds = 880.613 FPS
4425 frames in 5.0 seconds = 884.852 FPS
4313 frames in 5.0 seconds = 862.413 FPS

Hello could you be more specific, how u installed the rewrite driver? I can't find any deb package on that site. I tried to use the long command which is in the text, but nothing changed , 3d is not working. It would help if u paste here the commands...

---

### Post by night-wing on 2009-06-06
You have to add the repo to your sources.list and just make

sudo apt-get update && sudo apt-get dist-upgrade in the terminal.

---

### Post by neo.patrix on 2009-06-06
[QUOTE=MBybee]4335 frames in 5.0 seconds = 866.891 FPS
4207 frames in 5.0 seconds = 841.207 FPS
4237 frames in 5.0 seconds = 847.233 FPS
4316 frames in 5.0 seconds = 863.157 FPS
4407 frames in 5.0 seconds = 881.325 FPS
4404 frames in 5.0 seconds = 880.613 FPS
4425 frames in 5.0 seconds = 884.852 FPS
4313 frames in 5.0 seconds = 862.413 FPS
[/QUOTE]

+1

That is as good as ATI Proprietary Driver on Intrepid :KS. Does Compiz work reasonably fine as well? Maybe we can develop an organsied How-To, atleast for ATI Mobility Radeon X1300 (M52) sounds like excellent solution.

---

### Post by daflame on 2009-06-07
> **Dan42 said:**
> It looks like someone _[here](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569)_ managed to fix this problem using the _[radeon-rewrite](https://launchpad.net/~xorg-edgers/+archive/radeon)_ driver, but my xorg-fu is not strong enough to figure out how to use & configure this :-(

I tried this repo and it seemed to work with glxgears and tremendously improve performance with desktop effects, but as soon as I tried to run other GL based programs like warzone 2100 or with wine, they hang the whole system and I have to hard power off the computer.

I suspect that the reason for this is the fact that these programs are probably complied against mesa.  Changing from mesa 1.4 to 1.6 breaks them.

So I backported the patch that fixes the 1.4 mesa libraries and it works great for me.  No crashes at all.

I gave the patch to Bryce Harrington and he added it to his ppa here:
[https://edge.launchpad.net/~bryceharrington/+archive/ppa](https://edge.launchpad.net/~bryceharrington/+archive/ppa)

Please test this patch.  It uses the current version of mesa 7.4.0 with ubuntu patches.

---

### Post by neo.patrix on 2009-06-15
To my greatest amazement, it worked flawlessly out-of-the-box with direct system upgrade Intrepid-->Jaunty, using Update Manager, as simple and as easy as it could be. Alright, I had some trouble with dblatex, lilypond, blah blah TeXLive packages but that is my own mess anyway, nothing that I could not fix with 3 extra hours in night. 

The results with "radeon-rewrite" and out-of-the-box driver is same now on glxgears, my guess is they have been integrated with latest release of mesa drivers. Finally, waiting 2 extra months for driver paid of well.

For Mobility Radeon X1300 (M52) , you can safely ignore posts about "radeon-rewrite" , it works well out-of-the-box.

---

### Post by notanerd on 2009-06-22
lspci | grep Radeon
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

My screen is pixelated and unusable. It looks the same when I try to run compiz on Intrepid or Hardy. I have attached a screen shot, I posted a seperate forum [http://ubuntuforums.org/showthread.php?t=1174589](http://ubuntuforums.org/showthread.php?t=1174589) about this but no one seems to be able to help. I have attached a screen shot of the problem

I use the open source drivers as fglrx was too slow and choppy with full screen videos

---

### Post by w2vy on 2009-06-29
> **Mark Phelps said:**
> There is no simple way to "revert back" to a prior Ubuntu version.  You have to save off what you can and reinstall.

However, you should be able to use the open source driver.  Check out the link below for details:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Before upgrading is it a good idea to test the open source driver as recommended in the link above, or not needed?

Something worth including in this thread...

If you upgrade and it does not work, how will you be able to recover?

tom

---

### Post by super kim on 2009-08-18
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro]

``````
$ glxinfo | grep direct
direct rendering: Yes

``````
$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

``````
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

``````
$ glxgears
7462 frames in 5.0 seconds = 1492.252 FPS
9161 frames in 5.0 seconds = 1832.067 FPS
9194 frames in 5.0 seconds = 1838.643 FPS
10319 frames in 5.0 seconds = 2063.755 FPS
7740 frames in 5.0 seconds = 1547.837 FPS
2697 frames in 5.0 seconds = 539.092 FPS
4773 frames in 5.0 seconds = 954.592 FPS

```i have just done a clean install of jaunty.
the driver that is installed with jaunty works, however any black area has white spots like stars, this is annoying.(see the screen shot _[here]("http://img41.imageshack.us/img41/6497/screenshot1uiq.png")_ you can check the original _[here]("http://www.shafe.co.uk/crystal/images/lshafe/Malevich_Black_Square_1913.jpg")_)

glxgears worked fine, however when the window was moved it left a trail which stayed until i activated the window behind it (_[screen shot]("http://img30.imageshack.us/img30/4269/screenshot2cvc.png")_). i have not yet tested the video as this is a clean install.

i will edit this post after all the updates. i will also test the video afterwards and report the performance.

i must say its a shame
--------------------------------------------------------------------------
updated everything including the ati driver.
i even made some changes to my xorg.conf

glxgears say:
```
$ glxgears
5888 frames in 5.0 seconds = 1177.015 FPS
5710 frames in 5.0 seconds = 1141.633 FPS
6697 frames in 5.0 seconds = 1339.333 FPS
6391 frames in 5.0 seconds = 1278.060 FPS
5453 frames in 5.0 seconds = 1090.535 FPS
6111 frames in 5.0 seconds = 1222.192 FPS
3764 frames in 5.0 seconds = 752.256 FPS
```everything else is the same.

has anyone else had the noise problem (visual noise) at first i thought it was just the dark areas but now i notice there are black spots in the light areas too!
i will search for anything about this but the ati driver works well enough for me, i still haven't tried the video playback yet i will let you know when i do.


----------------------------------------------------------------------

ok i have tested video playback and it is perfect! personally i only want 2d from my computer (i have an xbox 360) so the only thing is the snow/stars/noise i have a theory... it is to do with visual effects because if i turn all the visual effects the noise goes too. i dont want the effects anyway, maybe in the future i can get them to to work without the screen noise but for now my graphics issues are **resolved**

oh here is my xorg.conf :)
```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Radeon 9500"
        Driver          "ati"
        Option          "AccelMethod"    "EXA"
        Option          "EnablePageFlip" "true"
        Option          "TripleBuffer"   "true"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9500"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
EndSection
#work, please please work this time
```

---

### Post by Mark Phelps on 2009-08-19
> **w2vy said:**
> Before upgrading is it a good idea to test the open source driver as recommended in the link above, or not needed?

Not only is that a good idea, it's also a good idea to check these forums to see if anyone else had a problem upgrading -- something very few folks seem willing to do.
> If you upgrade and it does not work, how will you be able to recover?
If you're talking about rolling back to the previous Ubuntu version, you will need to reinstall to do that -- another reason to do some research before doing an upgrade.

If you're talking about recovering from a bad video driver install, you can remove the restricred driver and replace it with the open source driver.  You will have to do that from a console using the command line, but it can be done without having to reinstall Ubuntu.

---

### Post by Torgas Prim on 2009-08-20
I just picked up an eMachines M6810 with the ATI Mobility 9600 in it. For giggles I booted to Jaunty knowing there were no drivers for the card. Nothing in the Hardware drivers list, so booted up 8.04 as it has ATI support for older cards...
Guess what? ATI drivers are no longer available anymore, even in 8.04.
I give up

---

### Post by zeusz4u on 2009-08-21
I have problems in Jaunty with my radeon XPress 1150 too. Does that radeon-rewrite solve my problem? Or at least increase the performance.

Here is the thread, i posted info about my card and details about performance :
[http://ubuntuforums.org/showthread.php?t=1137467&page=5](http://ubuntuforums.org/showthread.php?t=1137467&page=5)

---

