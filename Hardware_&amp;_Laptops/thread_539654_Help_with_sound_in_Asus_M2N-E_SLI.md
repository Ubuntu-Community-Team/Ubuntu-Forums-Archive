---
title: "Help with sound in Asus M2N-E SLI"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by GrayFoxi0n on 2007-08-31
I managed to scape from my last laptop, that has an ATI video card for obvious problems with compiz...
I just bought a new computer with an Asus M2N-E SLI motherboard, nForce 500 chipset and i dont get the sound properly working.
When i play Music, like MP3s it works fine, even i cannot play any oter video or whatever, but i still can work around it...
When i see some movie, i can heard the audio properly,
But i still cannot heard the system events sounds, and is a bit annoying the fact of not being able to play two sounds in the same time..... 

xi0n@Nostromo:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Aug 31 2007 for kernel 2.6.20-16-generic (SMP).
xi0n@Nostromo:~$ 


My ALSA version is updated, so, i dont really know what to do next..... will i have to wait for future Kernels??? :confused:

P.S.: My system is Ubuntu Feisty Fawn 7.04 x86 (non 64)

---

### Post by eggdeng on 2007-09-01
Post the output of ```
aplay -l
``` (That's a lowercase L, not a 1).

---

### Post by Julianito on 2007-09-01
Hi,

I have the same problem but on an AMD-64 bit distrib.
My motherboard is M2N-E SLI
And I have no sound The integrated audio card doesn't seems to work.
Except in Wine, playing game, I have sound.

Here is my aplay -l output :

**** Liste des PLAYBACK périphériques ****
carte  1: default [PnP Audio Device        ], périphérique 0 : USB Audio [USB Audio]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

---

### Post by eggdeng on 2007-09-01
Just to make sure I understand you, you have sound working through a set of usb speakers, and only have problems playing games on Wine? 
I don't know enough about Wine to help you with this. It could even be a game specific issue. Try ```
lspci
``` to see if you can identify the onboard sound card.

---

### Post by Julianito on 2007-09-01
.

---

### Post by Julianito on 2007-09-01
No, in fact, it is the opposite :
sound works fine in windows games using wine
but in ubuntu, I have no sound; using the sound settings :
- test sound crashed with automatic setting,
- with "usb audio" I have a bip but no real sound (like opening session, ...)
- with "alsa" and others, I have no sound but an error : "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Impossible d'ouvrir la ressource pour écriture."
The peripheral appears as "PNP Audio device (alsa mixer)"
I wine, the sound settings are : alsa (and in details : usb audio !)

~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0400 (rev a1)

~$ alsamixer 
alsamixer: function snd_ctl_open failed for default: No such device

Thanks for helping

---

### Post by eggdeng on 2007-09-02
OK. What seems to be happening is that your onboard sound card is being detected as a usb device. A forum search shows that this is a common problem with your particular motherboard. There doesn't seem to be any fix available just yet but you will find some suggestions at [http://ubuntuforums.org/showthread.php?t=517767&highlight=Asus+M2N-E+SLI]("http://ubuntuforums.org/showthread.php?t=517767&highlight=Asus+M2N-E+SLI")
Sorry not to be of more help & good luck.

---

### Post by Amazona aestiva on 2007-09-02
I have the same motherboard(M2N-E SLI) from ASUS, and I've never got sound at all. However Ubuntu detects an USB Audio Device.
I bought a Sound Blaster from Creative labs.

---

### Post by Julianito on 2007-09-08
If it can help to solve my problem, reading a flash movie in firefox, I got these errors :
```

ALSA lib ../../src/confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
ALSA lib ../../src/confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device

```
I just can't understand why/how my sound card works while playing World of Worldcraft (windows xp version) lauched with wine but doesn't in Ubuntu (without wine) !
Is there some windows drivers used by wine that work better (in recognizing my motherboard and its onboard sound card) than ubuntu drivers ?!
If so, please Ubuntu developers, work on it; I'm going to be crazy, or just deaf ;-)

---

### Post by gabor on 2007-09-14
hi, i think i have the solution..

the problem is, that alsa lists your card as number "1", and not number "0".

number "0" is the default card, and that's what most programs expect to use.

this is what i did to achieve it:

1. edit the /etc/modprobe.d/alsa-base file (as root),
2. find the line which contains snd-usb-audio.
3. comment it out, or simply delete it.
4. restart your computer

now everything should work correctly.

(basically, it seems that alsa is configured so that it does not allow the "usb sound card" to become the default card. and, somehow, our sound-card is detected as usb-sound-card. these instructions simply remove that restriction from alsa)

i found this when reading this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Julianito on 2007-09-14
And that... works !
Gabor, you are wonderful ! Thanks a lot !
I thought I'll have to wait until the gutsy, hope that they will add support for my mohterboard. Now, thanks to you, I'm happy :)

---

### Post by tzulberti on 2007-09-15
Can you listen to more than one thing at the time?
For example, while I'm using Amarok, I couldn't hear the beep of gaim/kopete...
That happens with the totem, and xmms...

---

### Post by martvi on 2007-10-01
Thanks. I had exactly the same problem, which is solved now.

---

### Post by Julianito on 2007-10-02
I still have some problems : 
[LIST]
[*]effectively seems to be some conflicts trying to use multiple softwares
[*]my microphone doesn't work
[/LIST]
But, Gutsy release is coming very soon (on the October 16 I guess) so we'll see if it's better...

---

### Post by Julianito on 2007-10-22
It seems I can't.

Using "automatic detection" in System/Prefs/sound I have this error :
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Impossible d'ouvrir la ressource pour écriture.

---

### Post by Julianito on 2007-10-22
And I cannot record sound

I now have a gutsy, nothing better with this sound issue

---

### Post by charrin on 2007-10-24
> **gabor said:**
> hi, i think i have the solution..

the problem is, that alsa lists your card as number "1", and not number "0".

number "0" is the default card, and that's what most programs expect to use.

this is what i did to achieve it:

1. edit the /etc/modprobe.d/alsa-base file (as root),
2. find the line which contains snd-usb-audio.
3. comment it out, or simply delete it.
4. restart your computer

now everything should work correctly.

(basically, it seems that alsa is configured so that it does not allow the "usb sound card" to become the default card. and, somehow, our sound-card is detected as usb-sound-card. these instructions simply remove that restriction from alsa)

i found this when reading this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Fantastic !!  I had installed Gutsy with this motherboard, I was wondering what could be happening with the sound and this trick worked immediatly !!

By the way, I have not tried yet to record sound or similar

Thanks a lot Gabor !!

---

### Post by Julianito on 2007-10-26
Hi all, for your information, I had some good results doing :
```
asoundconf list
asoundconf set-default-card default

```
with default is the result of the first command.

Now, detection is ok but I still can't record sound. 
TeamSpeak doesn't work : no sound hear or recorded

:~$ lsmod | grep snd
snd_rtctimer            5216  0 
snd_usb_audio          96640  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         12560  1 snd_pcm
snd_usb_lib            20352  1 snd_usb_audio
snd_hwdep              12168  1 snd_usb_audio
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  12 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
usbcore               161584  8 snd_usb_audio,snd_usb_lib,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

:~$ lsusb
Bus 001 Device 005: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp. 
Bus 002 Device 001: ID 0000:0000

---

### Post by uteck on 2008-04-01
> **gabor said:**
> hi, i think i have the solution..

the problem is, that alsa lists your card as number "1", and not number "0".

number "0" is the default card, and that's what most programs expect to use.

this is what i did to achieve it:

1. edit the /etc/modprobe.d/alsa-base file (as root),
2. find the line which contains snd-usb-audio.
3. comment it out, or simply delete it.
4. restart your computer

now everything should work correctly.

(basically, it seems that alsa is configured so that it does not allow the "usb sound card" to become the default card. and, somehow, our sound-card is detected as usb-sound-card. these instructions simply remove that restriction from alsa)

i found this when reading this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Thanks.  Now I just need to get kmix to control the correct volume.

---

### Post by bayhlon on 2008-05-04
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rory@Steele:~$ lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: 66MHz, fast devsel, IRQ 3
	I/O ports at fc00 [size=32]
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at feb00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:815a
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at e800 [size=16]
	Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d400 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c000 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=128
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdf00000-fdffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 812a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at bc00 [size=8]
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

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

01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ac00 [size=128]
	Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Unknown device 2252
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9c00 [size=128]
	Expansion ROM at fbfe0000 [disabled] [size=128K]
	Capabilities: <access denied>
how can i get my sound to work i am beginner so plz step by step lol

---

