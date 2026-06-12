---
title: "audio on HP Pavillion DV4z"
date: 2008-11-06
forum: Hardware
---

### Post by bongtothesoo on 2008-11-06
This problem has been solved. Thanks balak for the solution

> **balak said:**
> Folks,

The solution is given in 
[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

Basically its fixed in the newest version of alsa but since it will take a few weeks/months for ubuntu to move to that version you will need to install it yourself. 

If you are comfortable with doing things in the command line and more importantly keeping track of what you did so that you can repeat it after a kernel upgrade, go ahead as given in the thread above. I have it working on my dv4 perfectly.

Hello,
I installed intrepid ibex on my dv4z and everything works great. The only thing that does not work, as far as I can tell, is the audio. I followed a couple advices directed toward the dv4t(intel) and the tx2500(amd)to get audio to work but the solutions provided in those threads did not work...

This is my aplay -l
> card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and this is my lspci -v
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: 92300000-924fffff
	Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: 91300000-922fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: 91200000-912fffff
	Prefetchable memory behind bridge: 0000000070000000-00000000700fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: 91100000-911fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 70100000-701fffff
	Prefetchable memory behind bridge: 0000000091000000-00000000910fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at 92508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at 92507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at 92506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at 92508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 92505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 92504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at 92508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: ata_generic, pata_acpi, pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at 92500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at 92400000 (32-bit, non-prefetchable) [size=64K]
	Memory at 92300000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 92410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 91200300 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 70000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: fast devsel, IRQ 17
	Memory at 91200200 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at 91200100 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at 91200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 137f
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 91100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	I/O ports at 2000 [size=256]
	Memory at 91010000 (64-bit, prefetchable) [size=4K]
	Memory at 91000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 91020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


It looks like I have two audio devices, but I don't know what to make of it. Anybody else using a HP dv4z having this problem?

---

### Post by bongtothesoo on 2008-11-06
Bump! can anybody help me?

---

### Post by gali98 on 2008-11-07
Did you add any lines to /etc/modprobe.d/alsa-base ?
this is necessary (at least on the tx2500 series. I don't know much about your specific laptop.)

Also your not supposed to bump a thread within 24 hours of the last post :)
Kory

---

### Post by bongtothesoo on 2008-11-08
oh I did not know about the 24 hour rule I'm sorry...
I did add lines to /etc/modprobe.d/alsa-base found in the forums that helped the tx2500 series but it did not do the trick... neither did the ones for the dv4t... hmm I guess nobody who has a dv4z uses ubuntu?

---

### Post by gali98 on 2008-11-08
Okay, so I searched your codec and these are all the options you could use in the form
option snd-hda-intel model=MODEL
where MODEL is one from the following list: (the model is ref, dell-d21, etc)
```
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
	  panasonic	Panasonic CF-74

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

```

Obviously there are quite a few, with no specific one for you.
First, just to check, go into the volume control and make sure nothing is muted.
If it still doesn't work, I suggest you start with the models, ref or generic.
If you still can't get sound then I guess start down the list and see if you can get anything to work.

A way to restart the sound when testing is to do the following commands:
sudo alsa force-unload
sudo modprobe snd-hda-intel

Hope this helps...
Kory

---

### Post by nithinphilips on 2008-11-08
I have a dv4z as well. While I haven't been able to get the laptop speakers to work yet, I *can* hear sound if I plug in an external speaker or headphones. 

@bongtothesoo: The two devices you have are normal analog output (HDA ATI SB) and audio over HDMI (ATI HDMI). In Windows, if you connect your dv4z to an HDTV or a monitor using an HDMI cable, you can hear audio on the TV as well as watch video. It's really nice. You no longer have to carry a bunch of cables. If you use the fglrx driver, this might also work in Ubuntu, although I haven't tried this yet.

---

### Post by gali98 on 2008-11-10
Guys the only thing I can suggest is to put in mail to their mailing list.
Here is some instructions I found.
```
 If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").

ALSA project homepage
       http://www.alsa-project.org

  ALSA Bug Tracking System
       https://bugtrack.alsa-project.org/bugs/

  ALSA Developers ML
       mailto:alsa-devel@alsa-project.org

```
If you do decide to send it in, I also suggest you also give them the /proc/asound/card0/codec*

Kory

---

### Post by stergh on 2009-01-03
Has anything been figured out.. I am having the same problem.

---

### Post by possessedskier on 2009-01-09
I have the same problem with sound on an HP dv4-1220us with an AMD Turion 64 X2 RM-72 processor.  I had no sound at all and was finally able to get it through the headphone jacks by running a script that upgrades to the latest version of Alsa.  The script and instructions can be found here:

[http://ubuntuforums.org/showthread.php?t=962695]("http://ubuntuforums.org/showthread.php?t=962695")

I'm starting to work down the list of model= options from a previous post to see if that works.

My laptop has an HDMI output jack that sends sound and video to a TV.  This works in Vista.  I haven't tried it in Ubuntu yet.  I have a suspicion that the sound is going there and muting the internal speakers.

---

### Post by balak on 2009-01-15
Any updates on this. 
possessedskier: I did not have to do anything to get the audio working through headphones..

dpkg -l | grep alsa-base
ii  alsa-base  1.0.17.dfsg-2ubuntu1       ALSA driver configuration files

---

### Post by aeleneski on 2009-01-17
Yes, I also have this problem. Sound through headphone jacks, but not through speakers. The only difference is I am using Kubuntu.

---

### Post by OpenMercury on 2009-01-21
Hello, I'm a noob.  Just got done installing Hardy on DV4-1222nr pretty much same as DV4-220us (previous post).  My sound works fine during initial installation.  Upon updating system, sounds stop working on Laptop itself.  At home I have a HP Docking station and while the laptop is docked, sound works beautifully.  I'm fairly certain that the sounds are coming through the headphone jacks (when not docked) but I haven't validated that either.

---

### Post by OpenMercury on 2009-01-28
> **OpenMercury said:**
> Hello, I'm a noob.  Just got done installing Hardy on DV4-1222nr pretty much same as DV4-220us (previous post).  My sound works fine during initial installation.  Upon updating system, sounds stop working on Laptop itself.  At home I have a HP Docking station and while the laptop is docked, sound works beautifully.  I'm fairly certain that the sounds are coming through the headphone jacks (when not docked) but I haven't validated that either.

I just upgraded to Intrepid and now the sound isn't coming out of the Dock (XB3000) nor the laptops internal speakers.  I DID manage to plug in a set of headphones and the sound IS coming through the headphones.  Still searching for a solution, just thought I'd post my findings.

---

### Post by balak on 2009-02-21
Folks,

The solution is given in 
[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

Basically its fixed in the newest version of alsa but since it will take a few weeks/months for ubuntu to move to that version you will need to install it yourself. 

If you are comfortable with doing things in the command line and more importantly keeping track of what you did so that you can repeat it after a kernel upgrade, go ahead as given in the thread above. I have it working on my dv4 perfectly.

---

### Post by bongtothesoo on 2009-02-22
hey thank you so much this worked beautifully with my dv4z.
now the only thing needed is to get the microphone to work.
thanks again

---

