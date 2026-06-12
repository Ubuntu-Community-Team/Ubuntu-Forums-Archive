---
title: "No sound on Ubuntu 10.10 - fresh install"
date: 2010-12-05
forum: Hardware
---

### Post by rossco on 2010-12-05
Hi all,

I'm having trouble identifying what is wrong with my sound on my media PC.  I was running Ubuntu 10.04 but due to the accumulation of much tinkering thought I would start with a fresh install of Ubuntu Maverick.  However in the process I've killed the sound.  I get nothing now.

The sound card is on board (Asus P5K-VM).  Currently I'm just trying to access analogue stereo.

I've looked at the sound guide sticky for this forum but it hasn't helped but I will include the outputs.

>  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> lspci -v

....

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Device 8277
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

.....

> lsmod
Module                  Size  Used by
binfmt_misc             7984  1
vboxnetadp              5267  0
vboxnetflt             14966  0
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
xfs                   766179  1
exportfs                4226  1 xfs
nvidia              10221046  38
snd_usb_audio         105567  1
snd_usbmidi_lib        21313  1 snd_usb_audio
snd_rawmidi            22207  1 snd_usbmidi_lib
snd_seq_device          6912  1 snd_rawmidi
gspca_zc3xx            47258  0
gspca_main             27688  1 gspca_zc3xx
saa7164                63391  0
joydev                 11363  0
lp                     10201  0
ppdev                   6804  0
snd_hda_codec_realtek   299524  1
asus_atk0110           12987  0
videodev               49359  1 gspca_main
v4l1_compat            15519  1 videodev
dvb_core              105239  1 saa7164
usbhid                 42062  0
snd_hda_intel          26019  2
tveeprom               14098  1 saa7164
v4l2_compat_ioctl32    12486  1 videodev
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
intel_agp              32144  0
parport_pc             30086  1
hid                    84678  1 usbhid
serio_raw               4910  0
parport                37032  3 lp,ppdev,parport_pc
snd_hwdep               6660  2 snd_usb_audio,snd_hda_codec
snd_pcm                89104  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_timer              23850  1 snd_pcm
snd                    64117  16 snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_seq_device,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
firewire_ohci          24679  0
floppy                 65299  0
firewire_core          54327  1 firewire_ohci
usb_storage            50372  0
crc_itu_t               1739  1 firewire_core
8139too                23197  0
8139cp                 20333  0
pata_jmicron            2771  0
mii                     5261  2 8139too,8139cp
sky2                   53371  0


---

### Post by lisar915 on 2010-12-05
Greetings Ubuntu users:

I also just upgraded from 10.04 to 10.10.  The sound was working for the post part in 10.04 even though my mic never worked.  Then all of the sudden all the sound stopped working in 10.04.  Now it still doesn't work in Ubuntu 10.10.  

My laptop is a Vaio PCG-K33.  My sound card is ALI 5451.  The chip is Realtek ALC203 rev. 0.  And, I'm using ALSA Mixer version 1.0.23

When I typed aplay -l in the terminal, I got the following:
> 
*** List of PLAYBACK Hardware Devices ****
card 0: A5451 [ALI 5451], device 0: ALI 5451 [ALI 5451]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
lisa@lisa-laptop:~$ 

---

### Post by lisar915 on 2010-12-05
lspci -v
-------------------------------------

> 00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e0600000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-ati
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: e0300000-e03fffff
	Prefetchable memory behind bridge: f0000000-f7ffffff
	Kernel modules: shpchp

00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
	Subsystem: Sony Corporation Device 8175
	Flags: medium devsel, IRQ 10
	Memory at 44010000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=256]
	Capabilities: <access denied>

00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at 8400 [size=256]
	Memory at e0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ALI 5451
	Kernel modules: snd-ali5451

00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
	Subsystem: Sony Corporation Device 8175
	Flags: medium devsel
	Kernel driver in use: ali1535_smbus
	Kernel modules: alim7101_wdt, i2c-ali15x3, i2c-ali1535

00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: alim7101_wdt, alim1535_wdt

00:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0406
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 44000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

00:0a.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 168, IRQ 4
	Memory at e0006000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 3c000000-3ffff000 (prefetchable)
	Memory window 1: 40000000-43fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

00:0a.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at e000b000 (32-bit, non-prefetchable) [size=2K]
	Memory at e0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

00:0a.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at e0007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

00:0c.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at e0009000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0c.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 64, IRQ 6
	Memory at e000a000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 132, IRQ 11
	Memory at e000b800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at 8080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_ali
	Kernel modules: pata_ali

00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, medium devsel, latency 64, IRQ 3
	I/O ports at 9000 [size=256]
	Memory at e000bc00 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device 8175
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 4
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at a000 [size=256]
	Memory at e0300000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e0320000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb

lisa@lisa-laptop:~$ 

---

### Post by TheAnachron on 2010-12-06
What about the alsamixer? Are all settings fine?

---

### Post by jsampaio57 on 2011-01-26
try gnome-alsamixer. will give access to all channels. Only with it I could make my digital radio work in the line input. Cheers...

---

