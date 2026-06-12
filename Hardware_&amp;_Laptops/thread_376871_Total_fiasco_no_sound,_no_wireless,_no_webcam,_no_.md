---
title: "Total fiasco: no sound, no wireless, no webcam, no modem..."
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by xaval on 2007-03-05
Hello,

(Extended description of my hardware and mental problems more down on the page).

I open this post because I'm unable to pass the second step of the [Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449").

When I type this in the first step:
  [INDENT]*[SIZE=1]aplay -l[/SIZE]*
[/INDENT] 
I get:
   [INDENT][I][SIZE=1]**** List of PLAYBACK Hardware Devices ****[/SIZE]
[SIZE=1]    card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog][/SIZE]
[SIZE=1]      Subdevices: 1/1[/SIZE]
[SIZE=1]      Subdevice #0: subdevice #0[/SIZE][/I]
[/INDENT] 
Second step. When I type:
   [INDENT]*[SIZE=1]lspci -v[/SIZE]*
[/INDENT] 
I get:

[INDENT][SIZE=1][I] 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: b0100000-b01fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 225
        I/O ports at 8440 [size=8]
        I/O ports at 8434 [size=4]
        I/O ports at 8438 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8400 [size=16]
        Memory at b0004000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 52000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 50
        Memory at b0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 50
        Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 50
        Memory at b0007000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]
        Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 82 [Master PriP])
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 233
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 8420 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, slow devsel, latency 64, IRQ 233
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0c, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: b0200000-b02fffff
        Prefetchable memory behind bridge: 50000000-51ffffff

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

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at b0120000 [disabled] [size=128K]
        Capabilities: <access denied>

08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at b0210000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 54000000-55fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at b0211000 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

08:01.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 225
        Memory at b0211400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at b0211800 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: medium devsel, IRQ 255
        Memory at b0211100 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>

08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 66
        I/O ports at a000 [size=256]
        Memory at b0211c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0418
        Flags: medium devsel, IRQ 58
        Memory at b0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>[/I][/SIZE]
[/INDENT]                           

Then, I try to follow the recommendations and I go to the BIOS to see if something is disabled or not, but there is nothing related to the sound card. So, maybe the answer is in the "lspci -v" command I've run.

[INDENT][I][SIZE=1]00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, slow devsel, latency 64, IRQ 233
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
[/SIZE][/I]
[/INDENT]  Can somebody tell me which is the sound card chipset? What do I have? ATI or ALI? I go to [[SIZE=2]http://www.alsa-project.org/alsa-doc/[/SIZE]]("http://www.alsa-project.org/alsa-doc/") and nothing matches with nothing.

I don't really know what to do. In the shop they told me that the laptop was Linux compatible and for the moment the reality seems to confirm the opposite.

No sound in my laptop. Many of you can think that I haven't browsed the forums, yet. That I'm lazy and I just want a quick response with no effort. I don't think so. I bought my laptop 10 days ago and I haven't stop to try to make Edgy run on it. I'm pale, tired, frustrated. I'm not going to suicide, but I promise you, this Edgy Eft is too much! Dapper Drake, Breezy Badger, Hoary Hedgehog and Warty Warthog were saint people if we compare them to Edgy. And the sound is not the only problem I have. Ubuntu Edgy doesn't communicates with my wireless card, nor my modem, nor my webcam. This is a very bad joke. I thought that as much new the distribution was much hardware support I will have. But it seems to be the opposite! I'm sure that more than the help of this forum, I need an spiritual guide, but let's start here.

The label of my laptop says:

ACER Aspire 5051AWXMi
-AMD Turion 64 Mobile Technology MK36 (2.0 Ghz, 512KB L2 cache)
-14.1" WXGA Acer CristalBrite LCD
-Up to 256 MB ATI Radeon Xpress 1100 HyperMemory
-120GB HDD
-DVD-Super Multi double layer
-1GB DDR2
-802.11b/g wireless LAN

So, what? I don't want to go back to Windows after 4 years of Ubuntu. What is happening to me? Is this normal or I have to throw the laptop to the bin? 

Thanks very much for the patience and thanks in advance for the help.

---

### Post by lamalex on 2007-03-05
did you try just installing dapper? as for access denied did you try running it as root? if not thats probably why.

---

### Post by xaval on 2007-03-05
Dear Iamalex,

I forgot to tell that God provide me with little intelligence. I don't understand easily the world of Linux...

What do you mean with "did you try just installing Dapper?" Do you mean that I have to unistall Edgy and install Dapper and start all the mess from zero?

Then... "as for access denied did you try running it as root? What do I have to run as root? I switch the computer and the sound doesn't works. How can I switch Ubuntu from the beginning  as root?

Sorry for so much ignorance in these few lines. And thanks for your mercy.

---

### Post by roamingo on 2007-03-13
I have almost exactly the same laptop (Acer 5052WXMi).

My wireless is working, although not perfect (connect is less stable than in Windows, has to be closer to the AP than in Windows), using the broadcom wirelss driver come with Edgy, but there is some extra steps that you must follow. You may start here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy) . My sound is not working and AFAIK no distribution supports this card yet, because ALSA and the mainstream kernel does not have support for this card yet. Webcam/card reader: very unlikely they will get supported in any Linux distributions.
BTW, I have Suspend mode working out of the box, but Hibernate does not work.
As soon as the sound card get supported, I will remove my Windows partition .... :)

$ sudo lspci -v
Password:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cff00000
        Capabilities: [44] HyperTransport: MSI Mapping
        Capabilities: [b0] #0d [0000]

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [b0] #0d [0000]
        Capabilities: [b8] HyperTransport: MSI Mapping
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [b0] #0d [0000]
        Capabilities: [b8] HyperTransport: MSI Mapping
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [b0] #0d [0000]
        Capabilities: [b8] HyperTransport: MSI Mapping
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel

00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [b0] #0d [0000]
        Capabilities: [b8] HyperTransport: MSI Mapping
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 66
        I/O ports at 8440 [size=8]
        I/O ports at 8434 [size=4]
        I/O ports at 8438 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0004000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 52000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]
        Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 82 [Master PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 225
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 8420 [size=16]
        Capabilities: [70] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0c, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0200000-c02fffff
        Prefetchable memory behind bridge: 50000000-51ffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2

08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at c0202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 54000000-55fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0203000 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

08:01.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0203400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0203800 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: medium devsel, IRQ 255
        Memory at c0203100 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 50
        I/O ports at a000 [size=256]
        Memory at c0203c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

08:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: AMBIT Microsystem Corp. TravelMate 2410
        Flags: bus master, fast devsel, latency 64, IRQ 58
        Memory at c0200000 (32-bit, non-prefetchable) [size=8K]

---

### Post by roamingo on 2007-04-05
Recently I managed to get my sound card work. Sound works fine with the snd_hda_intel driver in alsa. The only thing that must be noticed is to
supply the options "probe_mask=3" when loading the driver. This can also be achieved
by adding "options snd_hda_intel probe_mask=3" on your modprobe.conf.

If you can only hear music using headphone, but nothing is going out from your speaker, try enable the "Surround" channel in your mixer.

Now the next big thing is to get the microphone to work, so that I can use Skype...

---

### Post by brendand on 2007-04-09
> Recently I managed to get my sound card work. Sound works fine with the snd_hda_intel driver in alsa. The only thing that must be noticed is to
supply the options "probe_mask=3" when loading the driver. This can also be achieved
by adding "options snd_hda_intel probe_mask=3" on your modprobe.conf.

Hi,

I would just like to say that the above option helped solve my problem which was a little different from the above.

My problem:  I was getting sound in the right channel only (Acer Aspire 5102WLMi) from my headphone socket.

My Solution:  I had no modprobe.conf file.  Instead I tried a scatter gun approach which came from trying other solutions.  I added this option to the following three files:
/etc/modprobe.d/alsa-base
/etc/modprobe.d/snd-hda-intel.modprobe
/etc/modules

I was so sick of trying things and rebooting my system that I didn't try to find the minimal solution, but I would try just adding the option to the above files one at a time in the order listed.

Thanks to those who posted in this thread.

Brendan

---

### Post by roamingo on 2007-07-11
Thanks Brendan.

Recently, I also manage to find out how to use my laptop for presentation using external projector (call it CRT below), without restarting X. I would like to share my experience here.

The hotkeys Fn+F5 in Windows can switch between LCD only, CRT only and LCD+CRT mode. This is extremely useful when you want to do some presentation. I am pretty sure Linux can also do this, but did not find out any easy way till very recently.

Mostly what I did is following the excellent post here: [http://tilmanfrosch.de/wp/index.php/2007/05/05/howto-make-a-ubuntu-linux-on-an-ibm-t41-thinkpad-work-with-an-external-widescreen-wxga-display/](http://tilmanfrosch.de/wp/index.php/2007/05/05/howto-make-a-ubuntu-linux-on-an-ibm-t41-thinkpad-work-with-an-external-widescreen-wxga-display/)

That is an IBM laptop and the author even managed to make the hotkey working. I did not go that far. Using scripts to control the switch without restarting X is enough for my current need. Here are the steps that I went through (if I recall correctly):

0. Save current xorg.conf (in case something goes wrong, go to rescue mode and copy back)

cd /etc/X11; sudo cp xorg.conf xorg.conf-before-using-fglrx

1. Install the fglrx driver and tools

sudo apt-get install xorg-driver-fglrx fglrx-control

2. Initialize xorg.conf to use the fglrx as the default video driver, and do a few setups.

sudo aticonfig --initial
sudo aticonfig --dtop clone

3. Restart X for the setting to take effect, and then to switch to LCD+CRT mode, use:

sudo aticonfig --enable-monitor=lvds,crt1

to switch to LCD only mode, use:

sudo aticonfig --enable-monitor=lvds

4. If the monitor/projector does not support the current video resolution, use xrandr (sudo apt-get install xrandr) to switch to another one:
bumpy:/etc/X11$ xrandr -s 2
bumpy:/etc/X11$ xrandr
 SZ:    Pixels          Physical       Refresh
 0   1280 x 800    ( 301mm x 192mm )   60  
 1   1280 x 768    ( 301mm x 192mm )   60  
*2   1024 x 768    ( 301mm x 192mm )  *60  
 3    848 x 480    ( 301mm x 192mm )   60  
 4    800 x 600    ( 301mm x 192mm )   60  
 5    720 x 576    ( 301mm x 192mm )   60  
 6    720 x 480    ( 301mm x 192mm )   60  
 7    640 x 480    ( 301mm x 192mm )   60  
 8    640 x 400    ( 301mm x 192mm )   60  
 9    640 x 350    ( 301mm x 192mm )   60  
 10   512 x 384    ( 301mm x 192mm )   60  
 11   400 x 300    ( 301mm x 192mm )   60  
 12   320 x 240    ( 301mm x 192mm )   60  
 13   320 x 200    ( 301mm x 192mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
bumpy:/etc/X11$ 

That's it. Hope it could be useful.
-- 
[http://www.ebanpo.com/roamingo](http://www.ebanpo.com/roamingo)
v4sw6CHSU$hw3pr7l6Ui2e8b5g4GPa31s5Mr1

---

