---
title: "Support Biostar TF7025-M2 TF7050"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by AchimRS on 2007-07-16
Hi,
I would like to use a Biostar TF7025-M2 Motherboard, because it seems to have a very low power consumption, a DVI port (or HDMI by TF7050-M2) and a COM port.

But do anyone have experiences under Ubuntu according this booard? It have the NVIDIA 7050 / 630 single-chipset, but is it supported???

Thanks a lot
  Achim

---

### Post by MajinCline on 2007-07-16
I just ordered the same mobo from newegg. From what I've been reading, the onboard network is not supported but everything else is supported. I can't speak from experience but I'm hoping that it is supported ok. This mobo will be used by my parents until eventually, when they upgrade, I'll get it so maybe by then it will be supported fully. Until then, if I want to install Ubuntu, I'll use a spare pci ethernet card if I can't manage to get the onboard one working.

---

### Post by TL_Mechanic on 2007-07-22
I just finished a build with the T7050 MOBO / Athlon 64 X2 3800+ / Feisty 7.04

Overall I'm pretty happy with the results.  I have had no issues with the on-board network.  It did cough a bit with the basic NVIDIA drivers.  I'm currently running with basic VESA driver.  From the NVIDIA web site, the 7050 chipset needs the 100.14.11 driver.  That's not currently in the "official" restricted driver as near as I can tell.  I haven't gotten around to trying a manual load.

My BIG issue has been the optical drive not mounting.  Reading the forums, it sound like this is a pretty common problem with the -16 kernel.  Trying to patch that is taking up my time right now.  It doesn't sound like a mother board or chipset issue.

Hope this helps.

Tony

---

### Post by jijin on 2007-07-25
Nvidia drivers do not see the onboard video card for me. I've pretty much given up until Gutsy is final.

Hopefully by then either the Envy method, the official nvidia drivers, or the restricted drivers will know how to find the onboard video because VESA drivers on widescreen sucks.

---

### Post by TL_Mechanic on 2007-08-02
Just a quick update to this thread.  I have gotten the 100.14.11 driver to fully work on the 7050 chipset.  I downloaded the driver from the NVIDIA website and installed using "Method 2" from "Latest nvidia feisty"

[[COLOR="Blue"]http://www.albertomilone.com/latest_nvidia_udsf_feisty.html[/COLOR]]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")

Added to that was additional drivers to add to the "Disabled_Modules" list in linux-restricted-modules-common.  This is shown in the following thread

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=499398[/COLOR]]("http://ubuntuforums.org/showthread.php?t=499398")

Now have viewing goodness on my wide screen.

Tony

---

### Post by pgroudas on 2007-08-08
I'm considering buying the same motherboard for use in a HTPC...have you tried out the hdmi output?  Can you dual monitor with it?

---

### Post by AlpineCarver on 2007-08-10
i've gotten the latest nvidia driver working, using a simpler procedure than i've seen posted. will post details soon.

unfortunately, the max resolution i can get thru the integrated geforce 7050PV gpu via the hdmi-to-dvi dongle is 1280x1024. i'm running a dell 2000fp monitor, which is native 1600x1200 pixels, but the nvidia control panel doesn't give me any resolution settings higher than 1280x1024.

can anybody help me get to 1600x1200 thru hdmi->dvi?

(this is on a biostar TF7050-M2, running ubuntu 7.04, with nvidia driver 100.14.11).

---

### Post by pgroudas on 2007-08-10
You can try manually editing your xorg.conf file to add those resolutions.  It defeats the purpose of the nvidia config applet, but its how I've managed to force intel drivers to behave in the past.

---

### Post by AlpineCarver on 2007-08-10
> You can try manually editing your xorg.conf file to add those resolutions.

i've tried adding 1600x1200 modes and metamodes, but to no avail.
i suspect the driver is not allowing it.
nvidia-settings reports the "native resolution" of my monitor as 1280x1024.

---

### Post by AlpineCarver on 2007-08-11
did some more research and tried some more things:

(1) installed the read-edid package, used nvidia-settings to generate an edid.bin for my monitor, and used parse-edid to generate an "Monitor" entry for xorg.conf.

(2) created a Modeline line from the same data and inserted it into the original Monitor section.

still no luck. can't display 1600x1200. max i can display is 1280x1024.

. . . frustrating!

---

### Post by AlpineCarver on 2007-08-11
i think i'm onto something...

when i extracted and parsed the monitor's edid info, it generated a 1600x1200 mode with a "DotClock" parameter of 162.000000 (MHz, i presume).

i ran nvidia-bug-report.sh, and found, in its copy of /var/log/Xorg.0.log, the following line:

    DELL 2000FP (DFP-0): 155.0 MHz maximum pixel clock

followed shortly by a list of "validated modes," which max out at 1280x1024.

so the driver thinks we don't have enough bandwidth to display 1600x1200. we need 162 MHz, and it thinks it only has 155 MHz. the question is: where is the 155 MHz limit coming from? it's not coming from the monitor. 162 MHz is within the monitor's published specs and is reported by the monitor in its edid info. could the nvidia 7050FV GPU be imposing this limit? that would be very disappointing....

---

### Post by AlpineCarver on 2007-08-11
problem solved. in /etc/X11/xorg.conf –

add the following line in the “Device” section for Driver “nvidia”:
[INDENT]Option "ModeValidation" "DFP-0: NoMaxPClkCheck”[/INDENT]

prepend the following string to the “metamodes” string in the “Screen” section:
[INDENT]1600x1200 +0+0;[/INDENT]

---

### Post by AlpineCarver on 2007-08-11
quick nvidia video driver install method that worked for me in ubuntu 7.04:

download NVIDIA-Linux-x86-100.14.11-pkg1.run from nvidia website
sudo /etc/init.d/gdm stop
hit CTL-ALT-F1 to get a login prompt
log in
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run

change last line of /etc/default/linux-restricted-modules-common to be:
[indent]DISABLED_MODULES="nv nvidiafb nvidia_new nvidia_legacy"[/indent]

---

### Post by AchimRS on 2007-08-12
Hi,
I tried the installation of the NVIDIA driver 100.14.11 using method 2 (from posting 5 in this thread).
I dont have any problems with wide-screen or high resolution, simply 1280x1024, but it simply don't work!!!

After reboot it dont start KDE, it ends up with the commandline login. If I start kde with "sudo /etc/init.d/kdm restart" it opens a black screen with a blinking cursor top left.

So I'm not able to use the drivers...

BTW: This posting is a litle bit of topic, I meanwhile bought a motherboard ASRock ALiveNF7G-HDready (also with the 7050/630 single chip)

Thanks to all experts
  Achim

---

### Post by AlpineCarver on 2007-08-12
> **AchimRS said:**
> I tried the installation of the NVIDIA driver 100.14.11 using method 2
. . .
but it simply don't work!!!

i haven't looked at method 2 in detail, but it seemed so long and involved that it might be easy to make a mistake.

if you are still using the biostar board, perhaps you could try the method in my post #13 above. it was pretty easy and worked for me.

---

### Post by AlpineCarver on 2007-08-12
on to the next problem...  networking is not functioning 100%.

about half the time, it works fine.
if i boot and it works, it will continue working until the next reboot.

every 2nd or 3rd reboot, i have no connectivity. i find this in var/log/syslog:
[indent]no DHCPOFFERS received[/indent]

runnning ifdown/ifup doesn't help. rebooting usually solves the problem.

the dhcp server is a netgear RP614v3, which is working flawlessly with many different devices.

**[COLOR="Red"]UPDATE - this problem has gone away. i don't know why, but it hasn't happened in a couple of weeks.[/COLOR]**

---

### Post by AchimRS on 2007-08-13
Hi AlpineCarver,
thanks for the response!
The method 2 acording the link above is basically the same as you explained in your post #13. In addition it installs some packages which are required (it seems you had it installed already).
I now added a new thread for this problem to prevent discussing it here (on the wrong board) because I now own an ASRock board:
[http://ubuntuforums.org/showthread.php?p=3181472#post3181472](http://ubuntuforums.org/showthread.php?p=3181472#post3181472)

Cheers
  Achim

---

### Post by matt_garman on 2007-08-20
> **AchimRS said:**
> Hi,
I tried the installation of the NVIDIA driver 100.14.11 using method 2 (from posting 5 in this thread).
I dont have any problems with wide-screen or high resolution, simply 1280x1024, but it simply don't work!!!

After reboot it dont start KDE, it ends up with the commandline login. If I start kde with "sudo /etc/init.d/kdm restart" it opens a black screen with a blinking cursor top left.

So I'm not able to use the drivers...

BTW: This posting is a litle bit of topic, I meanwhile bought a motherboard ASRock ALiveNF7G-HDready (also with the 7050/630 single chip)

Thanks to all experts
  Achim

Try this: when you reboot, go into a console and do the following:
```
$ sudo /etc/init.d/kdm stop
$ sudo rmmod nvidia
$ sudo modprobe nvidia
$ sudo /etc/init.d/kdm start
```

I have the exact same problem you do, though I'm using gdm/Gnome instead of kdm/kde.  For some reason, I can't get X to start unless I unload and then reload the nvidia module.

Does this extra info give anyone any idea what might be wrong?

Thanks,
Matt

---

### Post by matt_garman on 2007-08-22
My problems were fixed by following the instructions posted earlier in this thread:

[quote="TL_Mechanic"]Added to that was additional drivers to add to the "Disabled_Modules" list in linux-restricted-modules-common. This is shown in the following thread

[http://ubuntuforums.org/showthread.php?t=499398](http://ubuntuforums.org/showthread.php?t=499398)[/quote]

---

### Post by HarshReality on 2007-09-02
Just out of curiosity what does your hardware info look like... I got the TF-7025 with the nForce 630a chipset and mine was lit up like an xmas tree with unknowns. I dont suppose anybody has a wonder fix for that?
Just for the hell of it, heres lspci for the board... make note that I have video solved (obviously) and the network does work out of the box, though not efficiently.
```

00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3409
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3409
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0

00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3409
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 5
	Region 0: I/O ports at fc00 [size=64]
	Region 4: I/O ports at 1c00 [size=64]
	Region 5: I/O ports at 1c40 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3409
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3409
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 23
	Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3409
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3409
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3409
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at f000 [size=16]
	Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation Unknown device 055c (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 820c
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: fd000000-fd0fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 5407
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 504
	Region 0: I/O ports at 09f0 [size=8]
	Region 1: I/O ports at 0bf0 [size=4]
	Region 2: I/O ports at 0970 [size=8]
	Region 3: I/O ports at 0b70 [size=4]
	Region 4: I/O ports at dc00 [size=16]
	Region 5: Memory at fe02a000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fd800000-fd8fffff
	Prefetchable memory behind bridge: 00000000fd700000-00000000fd7fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:0f.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fd600000-fd6fffff
	Prefetchable memory behind bridge: 00000000fd500000-00000000fd5fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: fd400000-fd4fffff
	Prefetchable memory behind bridge: 00000000fd300000-00000000fd3fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:11.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fd200000-fd2fffff
	Prefetchable memory behind bridge: 00000000fd100000-00000000fd1fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:12.0 VGA compatible controller: nVidia Corporation Unknown device 053e (rev a2) (prog-if 00 [VGA])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 1406
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 2305
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at ac00 [size=256]
	Region 2: Memory at fdcff000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at fdb00000 [disabled] [size=128K]
	Capabilities: <access denied>

```

Incidentally this was with the latest and greatest Gutsy ISO (live mode)

---

### Post by HarshReality on 2007-09-03
OK, so this thread is becoming my blog....

I contacted biostar and sent my lspci and explained my issues and here is hte correspondance:

```

Question:
Linux drivers, resolution has been found for video. What about the rest of the board? You made the thing, one would think youd be able to get it to run efficiently in something other than windows....

Response:
Dear Customer,
Can you try to run Fedora Core 7 linux on this board ? So far, the Linux is open source code, difficult to control via manufactures. However, you should able to run it under Fedora Core 7 version.

Thank you very much.
=======================================================
With Best Regards
Paul Lee
Biostar FAE
Phone:886-2-22180150  ext290
E-Mail: paullee@biostar.com.tw
Website: http://www.biostar.com.tw

My Response:
Im just a bit curious.. have you ever used linux or did you just pull fedora out of the air since its a redhat base and one of the better known distrobutions? Same issues, ironically when I went to nVidia about a linux driver they turned it back and said the manufacturer was responsible for software application for a product even though the product was constructed with their chips.

Response:
Dear Customer,

In fact, we even contact with nVidia about onboard LAN, Audio and VGA Linux driver support. They has to recommend us to use Linux Kernel version 2.6.20 or later version. This is why we want you to install RedHat Fedora Core 7 last version. nVidia does not prepare Linux Driver due to it is open source. But, they said 2.6.20 should be included them. Last, can you let us know what troubles you face ?

<< Note >>
The following mail just for your reference. It is reply from nVidia.

Thank you very much.
=======================================================
With Best Regards 
Paul Lee
Biostar FAE
Phone:886-2-22180150 ext290
E-Mail: paullee@biostar.com.tw
Website: http://www.biostar.com.tw
=======================================================


-----Original Message-----
From: Spencer Kuo
Sent: Wednesday, August 29, 2007 7:30 PM
To: 'kmlin@biostar.com.tw'
Cc: avincent@aptek.com.tw; Ellis Chen; Grace Hsu; Julie Tseng; KF Cheng; 
Subject: RE: 8/29: Nvidia linux drivers D/L

KM.
We only provide the display driver. Rest of them is using the inbox driver. Currently, the Linux Kernel version is 2.6.20 will support  our chip.
For the Linux driver release we still go through the NV online.

Thanks
Spencer

Mine:
THe current applicable nForce drivers are for 400 series only, your pushing 630a this is mainly why issues report as unknown and the system doesnt know what to do with them. You NEED to put your heads together and  come up with an updated driver set so the southbridge is used efficiently rather than sitting as "unknown".

```

---

### Post by romain2k on 2007-09-03
I set up a TF7050-M2 with Ubuntu Feisty a week ago. In "lspci -v" output I see the "unknowns" that others have reported, though things basically work. I've consolidated the recordings from two earlier MythTV boxes on the new machine, though I have a few issues I'm still trying to resolve.

1. The "Line in" header on the M/B does not work for me.  I want to run the version of xmcd that you get in the Ubuntu repositories, but it's totally silent.  KsCD and newer xmcd can play using digital audio extraction instead of the analog connection, but they don't have the other functions I need.

2. A second issue is that even though I have the COM port working with a modem (AT commands work, and I see "RING" on an incoming call) WOR (wakeup on ring) doesn't work if the machine is powered off.

Does anyone have either (1) or (2) working with Linux of any kind?

BTW, other elements of the machine (also mentioned earlier on ubuntu-users email)
- N68pm716.bst BIOS update
- SATA ports configured as "Linux AHCI"
- AMD X2 4400 (Brisbane)
- 2x1G Crucial Ballistix RAM
- SATA1: Seagate ST3300622AS, 300 GB
- SATA2: Samsung HD501LJ, 500 GB
- Hauppauge PVR500MCE
- pcHDTV HD3000
- Antec NSK2400 case
- Thermaltake Blue Orb II CPU cooler

The system is running pretty cool, so I may try inserting a fan control to quiet the CPU cooler even more.

In retrospect, the TF7025-M2 might have been a better choice for me since it's cheaper you can run 1920x1200 through the DVI port.  The 7050 HDMI is apparently limited to 1920x1080, and I'll be using a computer monitor for the foreseeable future.  (I am currently using 1600x1200 VGA right now, because the DVI interfaces on both a Dell and a Samsung went weird on me).

Thanks,
Romain

---

### Post by AlpineCarver on 2007-09-03
[reply to HarshReality]

when i invoke "hardware info" from the gnome menu or "lspci" from the command line, i also get a lot of "unknowns", however my system (biostar TF7050-M2, ubuntu feisty 7.04) appears to be 100% healthy, at least for everything i've tried so far.

do these "unknowns" represent major functionality that is certainly broken, like support for devices i just haven't yet tried, or are they simply a reporting mechanism, for which nobody has gotten around to filling in lots of details?

w.r.t. your interaction with biostar: "what about the rest of the board?" is so vague as to be meaningless. if you're experiencing real problems in actual usage, beyond just some "unknowns" in an information panel, you should describe them in detail. that would give biostar something specific to work on.

---

### Post by AlpineCarver on 2007-09-03
> **romain2k said:**
> 
1. The "Line in" header on the M/B does not work for me.  I want to run the version of xmcd that you get in the Ubuntu repositories, but it's totally silent.  KsCD and newer xmcd can play using digital audio extraction instead of the analog connection, but they don't have the other functions I need.


i can successfully get audio in thru the "line in" jack on the exposed I/O panel. i haven't tried any motherboard headers. i also haven't used any of the apps you're using. i used audacity to capture voice-quality audio from an old portable cassette walkman, and it worked well.

---

### Post by viper104 on 2007-09-03
My setup is running XP Pro dual booting with KUBUNTU 7.04. I'm using the Biostar TF7050-M2 motherboard. I've had no problems getting anything to work in XP Pro, including HDMI audio.

KUBUNTU 7.04 (Fiesty Fawn) is another story. The video does not work on a straight install, so I had to install using the "alternative" installation cd. When it boots to the prompt, I had to type "nano -w /etc/X11/xorg.conf" and change the "nv" under Display to "vesa". Type "exit" and the startup will continue. That allowed me to boot into graphical  KUBUNTU.

I found that my network functionality was broken. The DHCP wouldn't work and I tracked it down to the hardware link being down. The fix for this was for me to boot into XP and go into the Device Manager. I went into the properties of the network card and into the advanced tab. Enable the Wake-on-lan setting. Hypothesis: I think XP was disabling the link chip on power down and turning it back on on startup, but kubuntu never turns it on.

Now that I have the internet I can focus on installing the nvidia drivers. I don't think I have any audio at this point either.

I hope this info helps someone. I spent hours debugging this.

---

### Post by HarshReality on 2007-09-03
> **AlpineCarver said:**
> [reply to HarshReality]

when i invoke "hardware info" from the gnome menu or "lspci" from the command line, i also get a lot of "unknowns", however my system (biostar TF7050-M2, ubuntu feisty 7.04) appears to be 100% healthy, at least for everything i've tried so far.

do these "unknowns" represent major functionality that is certainly broken, like support for devices i just haven't yet tried, or are they simply a reporting mechanism, for which nobody has gotten around to filling in lots of details?

w.r.t. your interaction with biostar: "what about the rest of the board?" is so vague as to be meaningless. if you're experiencing real problems in actual usage, beyond just some "unknowns" in an information panel, you should describe them in detail. that would give biostar something specific to work on.

I did that (was in an email beyond that post) moving 100 meg of files across my home network and it reporting 2 hours is totally unacceptable. Despite the "known or unknown" status if the system cant identify it then it obviously wont be able to utilize it to its full potential. From my perspective, I dont go looking for full priced batteries that have only 1/2 a charge. I know that some things will and wont but everything on this board is routed through the southbridge which is an nVidia chipset. To have that much that the system just doesnt know how to contend with is rediculous.

---

### Post by AlpineCarver on 2007-09-03
> **HarshReality said:**
> I did that (was in an email beyond that post) moving 100 meg of files across my home network and it reporting 2 hours is totally unacceptable. Despite the "known or unknown" status if the system cant identify it then it obviously wont be able to utilize it to its full potential. From my perspective, I dont go looking for full priced batteries that have only 1/2 a charge. I know that some things will and wont but everything on this board is routed through the southbridge which is an nVidia chipset. To have that much that the system just doesnt know how to contend with is rediculous.

ok, so you have a severe networking performance problem. i'm not up on any networking problems with these boards, except an intermittent dhcp problem i had when i was first bringing up the system, which appears to have somehow resolved itself.

my networking performace is fine. i haven't benchmarked it, but it doesn't feel sluggish. i just now dragged and dropped a 300 MB file into an NFS folder, and it took maybe 10 secs.

the one time i asked a question on **[the networking forum](http://ubuntuforums.org/forumdisplay.php?f=136)**, i got quick and competent help. perhaps you could try there.

---

### Post by junster on 2007-09-04
I figured out the networking problem.. it is basically not detecting the speed and duplex on boot. 

I set my interfaces file up like this to fix this problem.

```
root@ubuntu:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up /usr/sbin/ethtool -s eth0 speed 1000 duplex full autoneg off

```

I am still having problems getting x to work, but I should have some time later this week to figure that out.

---

### Post by HarshReality on 2007-09-04
Well, it would seem the major glitch (and I really hate to say this) is going to rely on nVidia.
It seems the nForce chipset has (at least in windows) a 'nForce PCI system management' so everything gets pumped through there. Thats why there seem to be devices in use but they are only 1/2 cocked since they are typically managed by the chipset. Google seems to say there is no current linux ditro with support for it.

Back to the waiting game....

junster:
The X issues have been identified and a fix posted *fumbles through numerous bookmarks*

Open a terminal window and 'modprobe -l | grep nvidia'

In my case (TF7025) I got 3 replies, most people return 4
nvidiafb
nvidia_new
nvidia_legacy

next 'sudo gedit /etc/default/linux-restricted-modules-common' and on the last line set it to read (additions will rely ony what modules your modprobe returned): DISABLED_MODULES="nvidiafb nvidia_new nvidia_legacy"

Then you should be good to load up 100.14.11 and go with it.

Of course this is for the VGA output, I havent tested the DVI-I interface and dont have it listed in my xorg. If anybody has gotten it going and would be willing to post the conf Id really be grateful (for the purposes of completeness)

---

### Post by AlpineCarver on 2007-09-04
i'm not an X expert, so i make no promises about the suitability of this for any purpose, but here is an xorg.conf that is working for me, using the built-in graphics of my biostar TF7050-M2 to drive a 1600x1200 monitor via DVI (using the hdmi-to-dvi adaptor that comes with the TF7050-M2).

note that i added the line:
    Option         "ModeValidation" "DFP-0: NoMaxPClkCheck"

and the following string near the bottom:
    1600x1200 +0+0; 


```


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2000FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7050 PV / NVIDIA nForce 630a"
    Option         "ModeValidation" "DFP-0: NoMaxPClkCheck"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x1200 +0+0; 1280x1024 +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection


```

---

### Post by HarshReality on 2007-09-05
So the board will drive two monitors? I have one LCD unplugged as it wouldnt fly in wondows... as a result I was under the impression you could only fire one or the other.

---

### Post by AlpineCarver on 2007-09-05
> **HarshReality said:**
> So the board will drive two monitors? I have one LCD unplugged as it wouldnt fly in wondows... as a result I was under the impression you could only fire one or the other.

i've only tried a DVI monitor; haven't tried the VGA port; don't know if it can do both simultaneously.

---

### Post by viper104 on 2007-09-05
> **HarshReality said:**
> So the board will drive two monitors? I have one LCD unplugged as it wouldnt fly in wondows... as a result I was under the impression you could only fire one or the other.

I have the 7050. I am able to drive 2 devices at once. I am using a Sony 17" monitor and a Syntax Olevia 32" LCD tv (model 532). After installing the Nvidia drivers successfully I just opened the "Nvidia Settings" under "System" and had it detect my displays. I am running kubuntu 7.04. The sony is on my vga, the olevia is hdmi.

---

### Post by HarshReality on 2007-09-07
OK, as I am on the 7025 it shouldnt be that much of a difference.... will have to pop it today and see what happens....

---

### Post by HarshReality on 2007-09-11
Well, found out why I couldnt go dual... the 7025 has a DVI-D which is digital only. Since my LCDs are analog...

---

### Post by HarshReality on 2007-09-11
Same here... so it would be a solid assumption that that would be the largest the chipset will support (my windows partition goes no higer either)

---

### Post by DROP on 2007-09-16
I am using the Biostar 7050-M2 and I can't get the xubuntu alternate or Gentoo live CD to detect any of the SATA hard disks I have connected to the board. I am booting them off of the SATA DVD/CD ROM drive connected to the same chipset.

Any ideas on what's going on with this?

thanks,
Ian

---

### Post by AlpineCarver on 2007-09-16
i had a sata device issue, though not exactly the same as yours. my sata optical drive worked properly with the live CD but not with the system after it was installed and booted from a hard disk.

the workaround was to go into the motherboard's BIOS settings and change the "SATA Operation Mode" from "IDE" to "AHCI".

for a list of all the problems i encountered and their solutions, [**click here**](http://ubuntuforums.org/showthread.php?t=530739).

---

### Post by DROP on 2007-09-17
Thanks for your help. I got the install CD to boot and recognize the SATA drives while booted to the install CD. But after the install finishes I don't even get to the grub menu when booting the hard drive. I still get the "No system disk found" message.
I have tried all of the bios options for the SATA operation mode and none of them allow me to boot the linux disk...
What is going on here?

---

### Post by phend-one on 2007-09-18
Has anyone got the network adapter to work? I had it working for a while. Anyone need to use the drivers off the Realtek website?

Right now the light for the network adapter just blinks orange. It's also having problems getting a DHCP lease from the server. 

Could this be because of shorewall?

---

### Post by DROP on 2007-09-19
For the network just use the r8169 driver from the kernel, that worked for me. Also if you are dual booting with Windows, make sure you have the "Wake-On-Lan after shutdown" option set to ENABLE on the network device in the Windows device manager.

Apparently by default it is set to disable, so when you shutdown, Windows disables the NIC and the Linux driver can't start it when you boot into Linux.

I still can't figure out why I can boot a Linux live cd in AHCI mode and I can't get grub to boot from the hard disk. In IDE mode I can't get either the CD or the hard disk to boot... Any ideas?

---

### Post by AlpineCarver on 2007-09-20
> **DROP said:**
> I still can't figure out why I can boot a Linux live cd in AHCI mode and I can't get grub to boot from the hard disk. In IDE mode I can't get either the CD or the hard disk to boot... Any ideas?

it's a long shot, but you could try moving your sata cable to a different sata connector on the MB.

i don't know if it's the case with this MB, but some have ports driven by 2 different chips with 2 different drivers on the same MB.

you can see a list of the sata devices i'm using successfully **[here](http://www.silentpcreview.com/forums/viewtopic.php?p=365030#365030)**

---

### Post by DROP on 2007-09-21
I could see all four of my drives from within the live CD anyway, and In this case I think they are all on the same controller. For some reason grub just won't start from the disk...

---

### Post by AlpineCarver on 2007-09-21
might make sense to start a new thread just about this issue. might attract attention from folks good at debugging this type of problem.

---

### Post by Crinos512 on 2007-11-11
I just bought a Biostar TF7050-M2 motherboard with an Athlon x2 64 4000+ processer and 2 sticks of 1GB [OCZ ddr2-800 PC6400 Platinum (rev. 2)]("http://www.ocztechnology.com/products/memory/ocz_ddr2_pc2_6400_platinum_revision_2") RAM, and I can't even seem to get the live disk to boot, the built in Memory test won't even run :(

I can't even worry about the SATA Hdd until I get passed this snafu.

Anyone have thoughts/suggestions on how to proceed from here? I can do an RMA, but I don't have any idea what part might be misbehaving.

---

### Post by Crinos512 on 2007-11-13
Bump?

Any advice?

---

### Post by jdkoola on 2007-11-21
> **Crinos512 said:**
> I just bought a Biostar TF7050-M2 motherboard with an Athlon x2 64 4000+ processer and 2 sticks of 1GB [OCZ ddr2-800 PC6400 Platinum (rev. 2)]("http://www.ocztechnology.com/products/memory/ocz_ddr2_pc2_6400_platinum_revision_2") RAM, and I can't even seem to get the live disk to boot, the built in Memory test won't even run :(

I can't even worry about the SATA Hdd until I get passed this snafu.

Anyone have thoughts/suggestions on how to proceed from here? I can do an RMA, but I don't have any idea what part might be misbehaving.

Don't know if you figured it out yet or not, but I was having the exact same problem.  The boot from the live CD would freeze up after it told me that it didn't recognize my Video Card.  I would manually select NVidia 7 series and my Dell monitor, then hit OK, then it wouldn't go any further.

I solved it by installing Mythbuntu using the "Safe Graphics Mode".

---

### Post by jdkoola on 2007-11-21
Well, I've run into a SNAFU.  I installed Mythbuntu 7.10 using the safe graphics mode as mentionned earlier.  I then proceeded to install the latest NVIDIA drivers from the NVIDIA website per instructions already posted in this thread.  Everything went great.  I was able to set new resolutions and everything.  

However, when I restarted the computer it was as if the changes I made had been erased, it started up with the same error that my graphics card and monitor could not be recognized and asked me if I wanted to run in Low Graphics Mode or configure the graphics driver and monitor manually.  I did so.  This time I went into the Restricted Packages Manager in the Mythbuntu menu and I found that the NVIDIA propietary drivers were already selected (they were not before, prior to me manually installing them).  So I deselected it, and then reselected it, at which point it downloaded and installed new drivers.  Once again, I was able to set custom resolutions and everything.

But when I restarted the same problem happened.

Any insights?

EDIT: I should note that Im using Mythbuntu 7.10, and to recap it's with a AMD 4000+ x2 brisbane, w/ 2 GB OCZ ram, on-board everything, a PCI wireless card and a PCI tuner card.

---

### Post by jdkoola on 2007-11-21
Sorry to bump, but really having trouble with this.  Thanks.

---

### Post by Crinos512 on 2007-11-21
I sent my board back via RMA... figured that if the built in Memtest wouldn't work there was something wrong with it.

I'll post here when i get it back and see if it works now.

---

### Post by DROP on 2007-11-22
A couple of things here.
If you are having issues with the motherboard and RAM, make sure that the two red LED's on the board are illuminated after post. If not **_MAKE SURE YOU KNOW THE RAM STICKS ARE WORKING_**. Try them in another board or something. I went through three motherboards before I realized that the RAM was the problem ...

Once you've dealt with that be sure you use the ALTERNATE (text-based installer) Ubuntu CD. Most likely the Xorg based installer won't work out of the box with the video card. (At least that is my experience) At a minimum, by using the alternate CD you'll be eliminating variables in dealing with other problems because you aren't using a more advanced graphical environment.

Here's my situation with installing Gutsy on this board.

When I have the MOBO in** IDE mode** in the BIOS:
- The CD installer will boot but **will NOT** detect the **hard drives**
- I am unable to boot Linux from the hard drive either

When I have the MOBO in **AHCI or Linux AHCI** mode:
- The CD installer will boot and detect all of the hard drives, I am also able to install the system to the hard drive from the CD (as one would expect)
-After reboot, however, I can not even get Grub to start. The BIOS spouts the message: "No System disk found, etc ..."

This situation is the case with other distros for me as well. I just can not get Linux to BOOT on this board.

---

### Post by DROP on 2007-11-22
> **jdkoola said:**
> Well, I've run into a SNAFU.  I installed Mythbuntu 7.10 using the safe graphics mode as mentionned earlier.  I then proceeded to install the latest NVIDIA drivers from the NVIDIA website per instructions already posted in this thread.  Everything went great.  I was able to set new resolutions and everything.  

However, when I restarted the computer it was as if the changes I made had been erased, it started up with the same error that my graphics card and monitor could not be recognized and asked me if I wanted to run in Low Graphics Mode or configure the graphics driver and monitor manually.  I did so.  This time I went into the Restricted Packages Manager in the Mythbuntu menu and I found that the NVIDIA propietary drivers were already selected (they were not before, prior to me manually installing them).  So I deselected it, and then reselected it, at which point it downloaded and installed new drivers.  Once again, I was able to set custom resolutions and everything.

But when I restarted the same problem happened.

Any insights?

EDIT: I should note that Im using Mythbuntu 7.10, and to recap it's with a AMD 4000+ x2 brisbane, w/ 2 GB OCZ ram, on-board everything, a PCI wireless card and a PCI tuner card.

Did you check that the xorg.conf file is in fact updated to use the restricted driver and updated settings?

---

### Post by Crinos512 on 2007-11-28
> **DROP said:**
>  **_MAKE SURE YOU KNOW THE RAM STICKS ARE WORKING_**.

I got the RMA'd Motherboard back and guess what?  still doesn't work. :mad:

Just submitted the RAM RMA request..... Cross your fingers! :wink:

---

### Post by jhetrick62 on 2008-01-12
I have the 7025 installed and running Gutsy on it with no issues.  I have 2gb of RAM.  I did not get the Restricted video driver running, but I downloaded  the Nvidia driver and installed it with no issues.  Just use the VESA driver temporarily until you can download and install.

No network issues here at all.

Jeff

---

### Post by Crinos512 on 2008-01-12
I am actually up and running now....

I needed to use the x64 Alternate install cd to get going but now i'm right as rain!

:)

---

### Post by Clochard on 2008-01-15
After much mucking about I'm also up and running Gutsy 64 on this board.  A few things I've learned (maybe someone has solutions?)

[LIST=1]
[*]You cannot dual boot on SATA without changing a BIOS setting (SATA mode from Linux AHCI to IDE so Windows on the IDE can boot)
[*]Gutsy alternate install resulted in an error as HALD and DBUS both were starting S12 in the init scripts.  The dual proc started too fast, borking it all.  Simply changing the hald to start S13 fixed that problem.
[*]I cannot boot with ACPI on.  I have had to edit grub to include acpi=off - which is a real shame.
[/LIST]

Knowing all this, I'm not sure I'd recommend this to a new Linux user as aboard of choice.  No ACPI kind of annoys me, and the amount of work I've had to do to get it working was inordinate.

---

### Post by Crinos512 on 2008-01-15
problem # 2 is due to **CONCURRENCY** being set equal to '**shell**' in /etc/init.d/rc, not the motherboard. 
...this doesn't occur if the setting is '**none**'

that said, I also am using **CONCURRENCY=shell**, and set hald to S13. :D



...as an aside I am currently running with the automated Overclock in the **V12** setting, making my 2.1 ghz Athlon 64 X2 4000+ run at 2.62 Ghz maximum. This places it just over the AMD Athlon 64 X2 5000+  which clocks @ 2.60 Ghz. I have a good heatpipe cooler on it and I stay below 109 F (~43 C) even under full load!  :D

---

### Post by Clochard on 2008-01-16
I saw that suggestion and checked to confirm that concurrency is set to none - it still is.  It has never been set to shell.  The problem was the init scripts.

Have you had any luck getting ACPI to work?  I'd love to use hibernate or suspend.

---

