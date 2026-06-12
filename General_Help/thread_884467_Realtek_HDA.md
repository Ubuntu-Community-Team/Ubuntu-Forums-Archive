---
title: "Realtek HDA"
date: 2008-08-09
forum: General Help
---

### Post by Uchiha_madara on 2008-08-09
My sound card is Realtek HDA i need to Configure it


what is the module for this device

this is "lspci" result
> mindstorm@mindstorm-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0100000-d01fffff
	Prefetchable memory behind bridge: d4000000-d7ffffff
	Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at d0004000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 10000000 [disabled] [size=512K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d0007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: 66MHz, medium devsel
	I/O ports at 8040 [size=16]
	Memory at d0004400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 88 [Master SecP])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, slow devsel, latency 64, IRQ 18
	Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

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
	Capabilities: <access denied>

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
	Capabilities: <access denied>

09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: Askey Computer Corp. Unknown device 7094
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>


and this is the alsa-base file i dont know what i shall write
the mpu_port and the index of the module??
> # install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388






---

### Post by PmDematagoda on 2008-08-09
The output of:-
```
lsmod | grep hda
```
should provide you with the required information.

---

### Post by Uchiha_madara on 2008-08-09
so ..

now  i have list of hda list

how can i install them to make my sound card works

---

### Post by logos34 on 2008-08-09
sudo modprobe snd_intel_hda

?

add it to /etc/modules list so it loads at boot

---

### Post by Uchiha_madara on 2008-08-10
I tried many times to insert the module

there is no result

i wondered that My friends have installed ubuntu hardy and ubuntu
Configure these modules Automatically for Laptops or Pc's

I don't know why this modules could not configured with me:(

---

