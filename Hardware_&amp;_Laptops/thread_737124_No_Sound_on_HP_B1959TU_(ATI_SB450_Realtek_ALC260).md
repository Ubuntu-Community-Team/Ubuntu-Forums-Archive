---
title: "No Sound on HP B1959TU (ATI SB450 Realtek ALC260)"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by Paps on 2008-03-27
Hullo,

First of all I would like to thanks anyone who will help or contribute in any way.

So here is my problem.

I'm trying since months to make my sound work in Ubuntu. No need to say that I have read countless post and tried all the solutions proposed thereafter.

Before that, the sound was working under Debian Lenny however, I had to leave Debian for Ubuntu as I do not have a broadband connection anymore...

So here is some output:

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Mar 18 2008 for kernel 2.6.22-14-generic (SMP).

$ cat /proc/asound/cards
 0 [SB ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0500000 irq 17

cat /proc/asound/devices
  0: [ 0] : control
  1: : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33: : timer

$ cat /proc/asound/oss/devices
  0: [0- 0]: mixer
  1: : sequencer
  3: [0- 0]: digital audio
  4: [0- 0]: digital audio
  8: : sequencer

$ cat /proc/asound/timers
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
  Client application 5971 : running
P0-0-1: PCM capture 0-0-1 : SLAVE

~$ cat /proc/asound/pcm
00-00: ALC260 Analog : ALC260 Analog : playback 1 : capture 1

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:07.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:07.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
08:07.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

$ lspci -nv
00:00.0 0600: 1002:5a31 (rev 01)
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 0604: 1002:5a3f (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0000000-c00fffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:04.0 0604: 1002:5a36 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        Memory behind bridge: 40000000-400fffff
        Capabilities: <access denied>

00:05.0 0604: 1002:5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:12.0 0101: 1002:4379 (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0507000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 40100000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 0c03: 1002:4374 (rev 80) (prog-if 10 [OHCI])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0504000 (32-bit, non-prefetchable) [size=4K]

00:13.1 0c03: 1002:4375 (rev 80) (prog-if 10 [OHCI])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0505000 (32-bit, non-prefetchable) [size=4K]

00:13.2 0c03: 1002:4373 (rev 80) (prog-if 20 [EHCI])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 0c05: 1002:4372 (rev 83)
        Subsystem: 103c:30ba
        Flags: 66MHz, medium devsel
        I/O ports at 8450 [size=16]
        Memory at c0507400 (32-bit, non-prefetchable) [size=1K]

00:14.1 0101: 1002:4376 (rev 80) (prog-if 82 [Master PriP])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8460 [size=16]
        Capabilities: <access denied>

00:14.2 0403: 1002:437b (rev 01)
        Subsystem: 103c:30ba
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 0601: 1002:4377 (rev 80)
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 0604: 1002:4371 (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 0300: 1002:5a62 (prog-if 00 [VGA])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 21
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 0280: 14e4:4312 (rev 01)
        Subsystem: 103c:1361
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 40000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

08:07.0 0c00: 1180:0832 (prog-if 10 [OHCI])
        Subsystem: 103c:30ba
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at c0200000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

08:07.1 0805: 1180:0822 (rev 19)
        Subsystem: 103c:30ba
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at c0200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:07.2 0880: 1180:0843 (rev 01)
        Subsystem: 103c:30ba
        Flags: bus master, medium devsel, latency 0, IRQ 15
        Memory at c0200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:07.3 0880: 1180:0592 (rev 0a)
        Subsystem: 103c:30ba
        Flags: medium devsel, IRQ 15
        Memory at c0201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:08.0 0200: 10ec:8139 (rev 10)
        Subsystem: 103c:30ba
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at a000 [size=256]
        Memory at c0201400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
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
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth 
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq 

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : 

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel probe_mask=9 model=hp

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC260

So here is what the log I can think to post sorry for the irrelevant one... If you need something else please do let me know.

Basicaly in alsamixer I have access to:
Master
Headphone
PCM
Speaker
etc

None of them work and I do get some error in dmesg. (for my full dmesg please go to: [http://paste.debian.net/51956](http://paste.debian.net/51956) lot of error from line 225 onward that I didn't get before...

I have tried to install alsa 1.0.14 same issue; no sound. Then, I have tried to install linux-backports-modules you probably guess the output; nosound.

Finally, I have installed the drivers on realtek websit (1.0.15) the one I'm using now.

Obviously, I have tried to play around with model=hp, hp-3013,basic,auto,etc and probe_mask=9,7,5, work the others don't.

I have also tried to mute and unmute some of the channel without success.

In Debian it worked by muting the "external amplifier" however, in Ubuntu no matter how many alsa source I compiled or install I cannot find the "external amplifier" option which I think is the solution as it is normally enabled when the drivers are installed even though it would work only if they aren't.

Therefore, I would like to know if someone could help me to get my sound working by either telling where I can find "external amplifier" cannot find it in alsamixer and gnomemixer or give me any solution that could work.

My notebook is a Compaq B1959TU

In advance, thank you for the time spent to read this post and for any intel you can give me.

Cheers

Paps

P.S. Merged double post

---

### Post by Paps on 2008-03-27
double post sorry

---

### Post by superprash2003 on 2008-03-27
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Paps on 2008-03-27
Thanks for the answer.

I have tried your solutions but unfortunately it doesn't work... 

By the way which channel should I use?

Master, PCM, Front or Speaker?

I already tried all... But no luck so far?

Any other suggestion?

Cheers

Paps

---

