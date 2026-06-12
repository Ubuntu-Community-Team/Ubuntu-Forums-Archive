---
title: "Please read this post to the end"
date: 2008-08-19
forum: General Help
---

### Post by Uchiha_madara on 2008-08-19
I can't recognize if the HDA is ATI, or INTEL
there is no sound in My Laptop
i write the command
lspci -l and this is the result
> 
root@mindstorm-laptop:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@mindstorm-laptop:~# lspci -v
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0100000-d01fffff
	Prefetchable memory behind bridge: d4000000-d7ffffff
	Capabilities: [b0] Subsystem: ATI Technologies Inc RS480 PCI Bridge

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at d0004000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 10000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: 66MHz, medium devsel
	I/O ports at 8040 [size=16]
	Memory at d0004400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 88 [Master SecP])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=0e, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d0200000-d02fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 21
	Memory at d4000000 (32-bit, prefetchable) [size=64M]
	I/O ports at 9000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d0211000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
	Memory window 0: 14000000-17fff000 (prefetchable)
	Memory window 1: 18000000-1bfff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001

09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at a000 [size=256]
	Memory at d0210000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: Askey Computer Corp. Unknown device 7094
	Flags: bus master, medium devsel, latency 168, IRQ 18
	Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2




and tried this Command aplay -L

> 
root@mindstorm-laptop:~# aplay -L
default:CARD=SB
    HDA ATI SB, ALC861 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC861 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC861 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC861 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC861 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC861 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC861 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)


and try this command lsmod
> 

mindstorm@mindstorm-laptop:~$ lsmod | grep hda
snd_hda_intel         344728  1 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd                    56996  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

root@mindstorm-laptop:~# nano /proc/asound/cards

#the result is :
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      


so please help me to find the true answer

---

### Post by loell on 2008-08-19
intel :)

---

### Post by unutbu on 2008-08-19
Uchiha_madara, your sig makes me laugh!

Here is what I get:
```

% lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```
```
% cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22
```
```

% aplay -L
default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```
So it looks to me like I have an Intel sound card.

If you search for the word "audio" in the output of lspci you get:
```

00:14.2 Audio device: **ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)**
Subsystem: Toshiba America Info Systems Unknown device ff31
Flags: bus master, slow devsel, latency 64, IRQ 17
Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

```
So it looks to me like you have an ATI sound card.

---

### Post by Saggy Peanuts on 2008-08-19
If the laptop was not a custom built one, then perhaps you could try to login to the manufacturers website and give the serial/product code of the laptop and it should give you the specs of the laptop as well as other useful tidbits.

---

### Post by coffeecat on 2008-08-19
I agree with **unutbu**. It looks as though you have an ATI card.

**Uchiha_madara**, don't worry that lsmod is telling you that the  snd_hda_intel kernel driver is loaded. Despite the name, it is the driver used for several makes of high-definition audio other than Intel, including ATI I believe. My Nvidia MCP61 HDA uses the snd_hda_intel driver.

---

### Post by Uchiha_madara on 2008-08-20
> **coffeecat said:**
> I agree with **unutbu**. It looks as though you have an ATI card.

**Uchiha_madara**, don't worry that lsmod is telling you that the  snd_hda_intel kernel driver is loaded. Despite the name, it is the driver used for several makes of high-definition audio other than Intel, including ATI I believe. My Nvidia MCP61 HDA uses the snd_hda_intel driver.

Ok My friend take a small Look for this Link

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

which step you advice me to work with ?

in anther Language what shall i do to make the sound works
in my Laptop?

---

### Post by markbuntu on 2008-08-20
This thread lists the setting options for your card which is ALC861 and tells you how to try them:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Uchiha_madara on 2008-08-24
There is no result ......

---

