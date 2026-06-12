---
title: "Problem with sound"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by syvehc on 2009-03-10
I can't get the sound to work in 8.10.  I tried three different sound card and read as many guides as I can.  I just tried in knoppix 6.10 and it works.  Please advise.  C-media is the card I have in now.

output for hardware

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f0000000-f3ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at bc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f4100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f4000000-f40fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05) (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: medium devsel, IRQ 11
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
	Subsystem: nVidia Corporation Device 0420
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9000 [size=128]
	[virtual] Expansion ROM at f3000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

02:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at a000 [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-cmipci

02:02.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Philips Semiconductors Device 0000
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f4000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 008a
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at a400 [size=256]
	Memory at f4001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

---

### Post by Neo_The_User on 2009-03-10
What happens when you try accessing the audio control panel? Right click on the speaker on your toolbar and select "Open Volume Control" and if you get the error about gstreamer, use a different kernel.

---

### Post by syvehc on 2009-03-10
I do get the error you are speaking of.  How do I get a different kernel?

---

### Post by Neo_The_User on 2009-03-10
heh. typical. compile one or download a different one via synaptic package manager. you should find at least 2 different kernels. try the 386 kernels. if that still has audio problems, use the -rt kernels. still doesn't work then use a kernel in synaptic that isn't a 2.6.27 kernel that is if you can find one. the gstreamer thing is a lie and means absolutely nothing.

---

### Post by syvehc on 2009-03-10
Thank you so much I found a different kernel during boot and every thing works.  The problem I was having was with 2.6.27.11 

2.6.27.9 works fine so I changed the file in grub to boot 2 rather than 0 and life is good.  I don't really understand it all so I am going to research different kernels and how it all works.  

I have been playing around with ubuntu off and on for a while now I am hoping to stick with it this time.  I hope this thread can help someone else out.

Thanks

---

### Post by Neo_The_User on 2009-03-10
No problem bud!

---

### Post by syvehc on 2009-03-11
I reinstalled the kernel with the synaptic manager like you said and like magic it all works with the 2.6.27-11-generic kernel.  I should have posted this problem days ago.  Kudos to you!!

---

### Post by Neo_The_User on 2009-03-11
Heh no problem. I compile kernels every week from git so I have experience with this sort of thing.

---

### Post by syvehc on 2009-03-11
Thanks, Neo.  The Ubuntu has me.  Follow the white rabbit

---

### Post by Neo_The_User on 2009-03-11
> **syvehc said:**
> Thanks, Neo.  The Ubuntu has me.  Follow the white rabbit

Hahaha! Knock, knock.

---

### Post by hamid2c on 2009-06-12
I had similar problems. I did an upgrade from ubuntu 6.06 to ubuntu 8.04.. The kernel I'm using is 2.6.24-24-generic. It seems that the alsa sound drivers haven't been compiled (or added) into some of the kernels.
However, I didn't download new kernels. I just compiled the latest version of alsa-drivers into my kernel.

You can follow the link below to do that:
[http://www.linlap.com/wiki/configuring+the+audio+and+updating+alsa+for+ubuntu+8.04]("http://www.linlap.co/wiki/configuring+the+audio+and+updating+alsa+for+ubuntu+8.04")

Don't forget to check the compatibility issues between your kernel and the alsa-driver you downloaded

---

