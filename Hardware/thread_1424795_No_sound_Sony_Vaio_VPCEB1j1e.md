---
title: "No sound Sony Vaio VPCEB1j1e"
date: 2010-03-08
forum: Hardware
---

### Post by Liakoni on 2010-03-08
I have installed Ubuntu Lucid 64bit 10.04 Alpha3 n my Sony Vaio VPCEB1j1e and i don't have sound. I insert line "options snd-hda-intel model=auto" in file  /etc/modprobe.d/alsa-base.conf. I also tried  "options snd-hda-intel model=vaio"  but no luck.
I tried kernel 2.6.33 but no luck.
I tried to play a .ogv video with mplayer and i am getting : bt_audio_service_open: connect() failed: Connection refused (111)


Command : "cat /proc/asound/card0/codec#* |grep Codec" gives 
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX

alsa-base:
  Installed: 1.0.22.1+dfsg-0ubuntu3
  Candidate: 1.0.22.1+dfsg-0ubuntu3
  Version table:
 *** 1.0.22.1+dfsg-0ubuntu3 0
        500 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/main Packages
        100 /var/lib/dpkg/status

---

### Post by leorolla on 2010-03-08
Run
```
alsamixer
```

Unmute and change volume of each device
```
sudo apt-get install alsaplayer
alsaplayer
```

Try playing a song.

If doesn't work
```
sudo apt-get remove pulseaudio
```
then reboot and tray again.

If doesn't work, paste the output of
```
lspci

```here

---

### Post by Liakoni on 2010-03-08
> **leorolla said:**
> Run
```
alsamixer
```

Unmute and change volume of each device
```
sudo apt-get install alsaplayer
alsaplayer
```

Try playing a song.

If doesn't work
```
sudo apt-get remove pulseaudio
```
then reboot and tray again.

If doesn't work, paste the output of
```
lspci

```here

I didn't have any luck with the above.
lspci:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by leorolla on 2010-03-08
Seems you have friends:
[http://ubuntuforums.org/showthread.php?t=1411914](http://ubuntuforums.org/showthread.php?t=1411914)

Show us this```

grep intel /etc/modprobe.d/*
modinfo snd-intel8x0
```And edit this```

sudo gedit /etc/modprobe.d/alsa-base.conf
```inserting what is in
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Setting_up_modprobe_and_kmod_support](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Setting_up_modprobe_and_kmod_support) at the top.

Then reboot.

---

### Post by Liakoni on 2010-03-08
> **leorolla said:**
> Seems you have friends:
[http://ubuntuforums.org/showthread.php?t=1411914](http://ubuntuforums.org/showthread.php?t=1411914)

Show us this```

grep intel /etc/modprobe.d/*
```

```
/etc/modprobe.d/alsa-base.conf:options snd-intel8x0m index=-2
/etc/modprobe.d/alsa-base.conf:options snd-hda-intel
/etc/modprobe.d/blacklist.conf:# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
/etc/modprobe.d/blacklist.conf:blacklist snd_intel8x0m
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist intelfb
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-intel8x0m

```
> **leorolla said:**
> modinfo snd-intel8x0
```
```
filename:       /lib/modules/2.6.32-16-generic/updates/alsa/snd-intel8x0.ko
license:        GPL
description:    Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455
author:         Jaroslav Kysela <perex@perex.cz>
srcversion:     1D7FD7C706CE3C0D8627E7E
alias:          pci:v000010B9d00005455sv*sd*bc*sc*i*
alias:          pci:v00001022d00007445sv*sd*bc*sc*i*
alias:          pci:v00001022d0000746Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd000000EAsv*sd*bc*sc*i*
alias:          pci:v000010DEd000000DAsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000008Asv*sd*bc*sc*i*
alias:          pci:v000010DEd00000059sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000006Asv*sd*bc*sc*i*
alias:          pci:v000010DEd0000003Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000001B1sv*sd*bc*sc*i*
alias:          pci:v00001039d00007012sv*sd*bc*sc*i*
alias:          pci:v00008086d00007195sv*sd*bc*sc*i*
alias:          pci:v00008086d00002698sv*sd*bc*sc*i*
alias:          pci:v00008086d000027DEsv*sd*bc*sc*i*
alias:          pci:v00008086d0000266Esv*sd*bc*sc*i*
alias:          pci:v00008086d000025A6sv*sd*bc*sc*i*
alias:          pci:v00008086d000024D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000024C5sv*sd*bc*sc*i*
alias:          pci:v00008086d00002485sv*sd*bc*sc*i*
alias:          pci:v00008086d00002445sv*sd*bc*sc*i*
alias:          pci:v00008086d00002425sv*sd*bc*sc*i*
alias:          pci:v00008086d00002415sv*sd*bc*sc*i*
depends:        snd-ac97-codec,snd-pcm,snd,snd-page-alloc
vermagic:       2.6.32-16-generic SMP mod_unload modversions 
parm:           index:Index value for Intel i8x0 soundcard. (int)
parm:           id:ID string for Intel i8x0 soundcard. (charp)
parm:           ac97_clock:AC'97 codec clock (0 = whitelist + auto-detect, 1 = force autodetect). (int)
parm:           ac97_quirk:AC'97 workaround for strange hardware. (charp)
parm:           buggy_semaphore:Enable workaround for hardwares with problematic codec semaphores. (bool)
parm:           buggy_irq:Enable workaround for buggy interrupts on some motherboards. (bool)
parm:           xbox:Set to 1 for Xbox, if you have problems with the AC'97 codec detection. (bool)
parm:           spdif_aclink:S/PDIF over AC-link. (int)
parm:           enable:bool
parm:           joystick:int

```
> **leorolla said:**
> 
And edit this```

sudo gedit /etc/modprobe.d/alsa-base.conf
```inserting what is in
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Setting_up_modprobe_and_kmod_support](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Setting_up_modprobe_and_kmod_support) at the top.

Then reboot.

Do you mean to copy-paste this to /etc/modprobe.d/alsa-base.conf ?
```
 # ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-intel8x0
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss

```

---

### Post by leorolla on 2010-03-09
Yes. To the top of the file.

Before that, could you show us
```
lspci -nn -v
lsmod
aplay -l

```
?

Then edit as above, reboot, and try again the fist steps.

If it doesn't work, show the same outputs please.

---

### Post by Liakoni on 2010-03-09
> **leorolla said:**
> Yes. To the top of the file.

Before that, could you show us
```
lspci -nn -v
lsmod
aplay -l

```
?

Then edit as above, reboot, and try again the fist steps.

If it doesn't work, show the same outputs please.

Without changing anything.
lspci -nn -v
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e080 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f600a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f6008000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f4c00000-f5ffffff
	Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f3800000-f4bfffff
	Prefetchable memory behind bridge: 00000000f6300000-00000000f64fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f2400000-f37fffff
	Prefetchable memory behind bridge: 00000000f6500000-00000000f66fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0400000-f23fffff
	Prefetchable memory behind bridge: 00000000f6700000-00000000f68fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f6007000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05) (prog-if 01)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 33
	I/O ports at e070 [size=8]
	I/O ports at e060 [size=4]
	I/O ports at e050 [size=8]
	I/O ports at e040 [size=4]
	I/O ports at e020 [size=32]
	Memory at f6006000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: medium devsel, IRQ 4
	Memory at f6005000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f6004000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e017]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4c00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f3802000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f3801000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.4 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f3800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4381] (rev 11)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f2420000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at b000 [size=256]
	Expansion ROM at f2400000 [disabled] [size=128K]
	Capabilities: <access denied>

3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0


```

lsmod
```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_intelhdmi    11463  1 
snd_hda_codec_realtek   317207  1 
snd_hda_intel          25338  2 
snd_hda_codec         103651  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7002  1 snd_hda_codec
snd_pcm_oss            47289  0 
snd_mixer_oss          15862  1 snd_pcm_oss
fbcon                  39270  71 
snd_pcm                95335  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
tileblit                2487  1 fbcon
snd_seq_dummy           1910  0 
snd_seq_oss            34786  0 
font                    8053  1 fbcon
snd_seq_midi            6149  0 
bitblit                 5779  1 fbcon
softcursor              1565  1 bitblit
snd_rawmidi            23795  1 snd_seq_midi
vga16fb                12693  0 
snd_seq_midi_event      7171  2 snd_seq_oss,snd_seq_midi
arc4                    1473  2 
snd_seq                61232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vgastate                9857  1 vga16fb
snd_timer              23593  2 snd_pcm,snd_seq
ath9k                 328853  0 
i915                  319868  3 
uvcvideo               62339  0 
snd_seq_device          6978  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              237700  1 ath9k
drm_kms_helper         30742  1 i915
ath                     9723  1 ath9k
snd                    77105  20 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
videodev               40422  1 uvcvideo
drm                   198930  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
soundcore               8052  1 snd
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
cfg80211              148386  3 ath9k,mac80211,ath
snd_page_alloc          8788  2 snd_hda_intel,snd_pcm
sdhci_pci               6700  0 
psmouse                64288  0 
intel_agp              29165  1 
video                  20623  1 i915
sdhci                  17928  1 sdhci_pci
output                  2503  1 video
serio_raw               4886  0 
sony_laptop            33756  0 
led_class               3732  2 ath9k,sdhci
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40860  0 

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Liakoni on 2010-03-09
After the changes no sound again...

lspci -nn -v
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e080 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f600a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f6008000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f4c00000-f5ffffff
	Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f3800000-f4bfffff
	Prefetchable memory behind bridge: 00000000f6300000-00000000f64fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f2400000-f37fffff
	Prefetchable memory behind bridge: 00000000f6500000-00000000f66fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0400000-f23fffff
	Prefetchable memory behind bridge: 00000000f6700000-00000000f68fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f6007000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05) (prog-if 01)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 33
	I/O ports at e070 [size=8]
	I/O ports at e060 [size=4]
	I/O ports at e050 [size=8]
	I/O ports at e040 [size=4]
	I/O ports at e020 [size=32]
	Memory at f6006000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: medium devsel, IRQ 4
	Memory at f6005000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f6004000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e017]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4c00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f3802000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f3801000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.4 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f3800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4381] (rev 11)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f2420000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at b000 [size=256]
	Expansion ROM at f2400000 [disabled] [size=128K]
	Capabilities: <access denied>

3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

```
lsmod
```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_intelhdmi    11463  1 
snd_hda_codec_realtek   317207  1 
snd_hda_intel          25338  2 
snd_hda_codec         103651  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7002  1 snd_hda_codec
snd_intel8x0           31375  0 
snd_ac97_codec        125751  1 snd_intel8x0
ac97_bus                1450  1 snd_ac97_codec
fbcon                  39270  72 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5779  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12693  0 
vgastate                9857  1 vga16fb
arc4                    1473  2 
snd_pcm_oss            47289  0 
snd_mixer_oss          15862  1 snd_pcm_oss
snd_pcm                95335  5 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1910  0 
snd_seq_oss            34786  0 
snd_seq_midi            6149  0 
snd_rawmidi            23795  1 snd_seq_midi
snd_seq_midi_event      7171  2 snd_seq_oss,snd_seq_midi
ath9k                 328853  0 
snd_seq                61232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              237700  1 ath9k
ath                     9723  1 ath9k
uvcvideo               62339  0 
videodev               40422  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
i915                  319868  3 
drm_kms_helper         30742  1 i915
v4l2_compat_ioctl32    12020  1 videodev
snd_timer              23593  2 snd_pcm,snd_seq
snd_seq_device          6978  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77105  22 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
sony_laptop            33756  0 
psmouse                64288  0 
serio_raw               4886  0 
intel_agp              29165  1 
soundcore               8052  1 snd
snd_page_alloc          8788  3 snd_hda_intel,snd_intel8x0,snd_pcm
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
cfg80211              148386  3 ath9k,mac80211,ath
led_class               3732  2 ath9k,sdhci
drm                   198930  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40860  0 

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by leorolla on 2010-03-09
sudo apt-get install linux-backports-modules-alsa-2.6.31-20-generic

reboot

Test sound

sudo modprobe snd-intel8x0

Test sound

---

### Post by Liakoni on 2010-03-09
> **leorolla said:**
> sudo apt-get install linux-backports-modules-alsa-2.6.31-20-generic

reboot

Test sound

sudo modprobe snd-intel8x0

Test sound

I have Ubuntu Lucid amd64 with 2.6.32-16-generic kernel.
I have tried linux-backports-modules-alsa-2.6.32-16-generic and linux-alsa-driver-modules-2.6.32-16-generic from ppa but nothing worked.
I even tried compiling alsa from source.

---

### Post by Liakoni on 2010-03-09
When i try to play a video or a song with mplayer i got this:
```
mplayer /usr/share/example-content/Ubuntu_Free_Culture_Showcase/water-and-wind.ogv 
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer UNKNOWN-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /usr/share/example-content/Ubuntu_Free_Culture_Showcase/water-and-wind.ogv.
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  320x176  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 Artist: Speedsound
 Album: Groove Connection - Promo
 Creation Date: 2008
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x7f898568c9a0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 320 x 176 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.82:1 - prescaling to correct movie aspect.
VO: [xv] 320x176 => 320x176 Planar YV12 
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   3.1 V:   1.5 A-V:  1.545 ct:  0.150  37/ 37  2%  1%  0.6% 0 0 
Exiting... (Quit)

```

With vlc:
```
 vlc /usr/share/example-content/Ubuntu_Free_Culture_Showcase/water-and-wind.ogv 
VLC media player 1.0.5 Goldeneye
[0x167f4b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x7f23d8002a38] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x7f23d8022208] pulse audio output: No. of Audio Channels: 2

```

---

### Post by leorolla on 2010-03-09
cat /proc/asound/version

---

### Post by leorolla on 2010-03-09
Did you try Kubuntu lucid alpha 3 live CD? This guy [http://forums.fedoraforum.org/showthread.php?p=1335892](http://forums.fedoraforum.org/showthread.php?p=1335892) has the same sound as you and he got it working.

For information: we are trying to see if something works, but support for your device is being developed right now... see implementations on the last couple of days:
[http://git.alsa-project.org/?p=alsa-kernel.git&a=search&h=HEAD&st=commit&s=alc269](http://git.alsa-project.org/?p=alsa-kernel.git&a=search&h=HEAD&st=commit&s=alc269)

So if you will try compiling ALSA from scratch, I doubt the 1.0.22.1 will be enough, I guess you already have it. You will need to compile the last revision from the git line...

---

### Post by Liakoni on 2010-03-09
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar  8 2010 for kernel 2.6.32-16-generic (SMP).

The intesting part is, that this laptop has pre-installed splastop, which is Linux based, and the sound works fine (i tried browsing youtube).

I know the platform is new and i am not complaing, i knew what I bought.

PS: Another intersting thing is ethernet is not supported. It will be supported in 2.6.33 kernel.

---

### Post by leorolla on 2010-03-09
> **Liakoni said:**
> cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar  8 2010 for kernel 2.6.32-16-generic (SMP).

The intesting part is, that this laptop has pre-installed splastop, which is Linux based, and the sound works fine (i tried browsing youtube).

I know the platform is new and i am not complaing, i knew what I bought.

PS: Another intersting thing is ethernet is not supported. It will be supported in 2.6.33 kernel.

You can test Kubuntu to see what it gives.

You can follow some of the "Build ALSA" guides you will find with google, but replacing the downloaded file by today's version from
[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/)

You can help reporting this bug and maybe tell them that it works with splastop:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934)


Edit:
To get the built-last-night ALSA, you can get a .deb file here:
[https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa/+sourcepub/989385/+listing-archive-extra]("https://edge.launchpad.net/%7Eubuntu-audio-dev/+archive/ppa/+sourcepub/989385/+listing-archive-extra")

---

### Post by Riot@ct on 2010-03-09
I have the same laptop but the live cd start only in graphic safe mode and the 3d not works in this mode.

Can I install Intel driver to work 3d?

Sorry for my english.

---

### Post by Liakoni on 2010-03-09
> **Riot@ct said:**
> I have the same laptop but the live cd start only in graphic safe mode and the 3d not works in this mode.

Can I install Intel driver to work 3d?

Sorry for my english.

In Ubuntu Lucid 10.04 3D works by default.
You can upgrade now, or wait 1 month for the official release of Lucid.

---

### Post by Riot@ct on 2010-03-09
> **Liakoni said:**
> In Ubuntu Lucid 10.04 3D works by default.
You can upgrade now, or wait 1 month for the official release of Lucid.
Ok, thank you. But if I want to use karmic must to use only vesa driver without 3d?

In Lucid the sound work?

---

### Post by Liakoni on 2010-03-09
> **Riot@ct said:**
> Ok, thank you. But if I want to use karmic must to use only vesa driver without 3d?

In Lucid the sound works?

No the sound is still a problem in Lucid:(
I didn't try Karmic, so i don't know about the 3d.

---

### Post by Riot@ct on 2010-03-09
> **Liakoni said:**
> No the sound is still a problem in Lucid:(

In any way? :(

---

### Post by Riot@ct on 2010-03-09
work the hotkey for screen brightness? I do not work.

---

### Post by Liakoni on 2010-03-10
> **Riot@ct said:**
> In any way? :(
They are trying to fix the problem.

---

### Post by Riot@ct on 2010-03-10
> **Liakoni said:**
> They are trying to fix the problem.
thank you.

I noticed the sound work in headphone but the volume is very very very low.

but work you the brightness hotkeys?

---

### Post by leorolla on 2010-03-10
> **leorolla said:**
> 
To get the built-last-night ALSA, you can get a .deb file here:
[https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa/+sourcepub/989385/+listing-archive-extra]("https://edge.launchpad.net/%7Eubuntu-audio-dev/+archive/ppa/+sourcepub/989385/+listing-archive-extra")

Did you test it?

---

### Post by Liakoni on 2010-03-10
> **leorolla said:**
> Did you test it?

i didn't have time to test it, when i do i will post it here.
But i see that the alsa developers are working on it.

---

### Post by Liakoni on 2010-03-10
I have [https://edge.launchpad.net/~ubuntu-audio-dev/](https://edge.launchpad.net/~ubuntu-audio-dev/) ppa on my sources.list to have daily updates. I noticed that i have very low sound from headphones.
From speakers nothing , but i am optimistic.

Fn keys works for sound and brigthness.

---

### Post by Riot@ct on 2010-03-10
> **Liakoni said:**
> I have [https://edge.launchpad.net/~ubuntu-audio-dev/](https://edge.launchpad.net/~ubuntu-audio-dev/) ppa on my sources.list to have daily updates. I noticed that i have very low sound from headphones.
From speakers nothing , but i am optimistic.

Fn keys works for sound and brigthness.
In Lucid the sound from headphones (very low) work without ubuntu-audio-dev ppa too.
But for me not work Fn keys for brightness (I use Kubuntu, you?).

I hope in alsa developers. :(

---

### Post by Liakoni on 2010-03-10
> **Riot@ct said:**
> In Lucid the sound from headphones (very low) work without ubuntu-audio-dev ppa too.
But for me not work Fn keys for brightness (I use Kubuntu, you?).

I hope in alsa developers. :(

I use Ubuntu

---

### Post by Riot@ct on 2010-03-10
> **Liakoni said:**
> I use Ubuntu
Ok, if you have good news for audio please post here.
I will do the same. :)

---

### Post by Liakoni on 2010-03-10
> **Riot@ct said:**
> Ok, if you have good news for audio please post here.
I will do the same. :)

I just test the microphone and it works :)

---

### Post by Riot@ct on 2010-03-10
> **Liakoni said:**
> I just test the microphone and it works :)
Great. This is up a step forward, I awaiting for new good :)

---

### Post by Riot@ct on 2010-03-11
Sorry if I'm still offtopic, but work you wireled connection?
Work me only wireless.

edit: I have read previous post, it's not supported, only for 2.6.33 :(

---

### Post by leorolla on 2010-03-11
My advise: use Lucid.

Your machine is two new, support for it is being developed right now, it is not present in Karmic.

Lucid will be a LTS release, once you install and set it, it will be there for years.

[http://cdimage.ubuntu.com/releases/lucid/alpha-3/](http://cdimage.ubuntu.com/releases/lucid/alpha-3/)

---

### Post by Liakoni on 2010-03-11
> **Riot@ct said:**
> Sorry if I'm still offtopic, but work you wireled connection?
Work me only wireless.

edit: I have read previous post, it's not supported, only for 2.6.33 :(

Yes, wired connection is supported only in 2.6.33 .
You can install it from here, if you like: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

---

### Post by Riot@ct on 2010-03-11
> **Liakoni said:**
> Yes, wired connection is supported only in 2.6.33 .
You can install it from here, if you like: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)
thank you, I will try. with 2.6.33 kernerl there is other improve.

@leorolla: I'm already using Lucid.

---

### Post by Cuppa-Chino on 2010-03-12
same here with a vaio vpceb1c5e

```
~$ lspci -v -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
```

```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf5e00000 irq 35
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0040000 irq 36

```

```
$ head -n 1 /proc/asound/card0/codec*
Codec: Realtek ALC269

```

very very low sound from headphones, no difference if using dev-ppa modules or not

have noticed that moving the sliders in alsa-mixer is currently "linked" ie when I change pcm master changes (not proportionally) - tried using dbmeasure but to be honest did not get what I need to do properly

---

### Post by Riot@ct on 2010-03-22
Any news about sound? :)

---

### Post by Cuppa-Chino on 2010-03-22
yes sorry forgot to post it here -- posted in a different thread on the issue

[http://ubuntuforums.org/showthread.php?p=9008912#post9008912]("http://ubuntuforums.org/showthread.php?p=9008912#post9008912")

that is only a temporary fix, needs to be executed every time you start up the computer (not every time you restart gnome mind you) but it works, am trying to find out what to do to get it patched in alsa.

---

### Post by Liakoni on 2010-03-23
> **Cuppa-Chino said:**
> yes sorry forgot to post it here -- posted in a different thread on the issue

[http://ubuntuforums.org/showthread.php?p=9008912#post9008912]("http://ubuntuforums.org/showthread.php?p=9008912#post9008912")

that is only a temporary fix, needs to be executed every time you start up the computer (not every time you restart gnome mind you) but it works, am trying to find out what to do to get it patched in alsa.

Thanks! Changing NODE 0x19 worked :D

---

### Post by fozzieb on 2010-03-24
Fantastic, works on my Vaio VPCEB1E0E

---

### Post by Riot@ct on 2010-03-26
Great, works fine!!!
Thank you very much!!! :popcorn:

---

### Post by Riot@ct on 2010-04-14
The issue has been fixed by [http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commit;h=ff818c24c2af370153646d302d831b69b023816f](http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commit;h=ff818c24c2af370153646d302d831b69b023816f)

---

### Post by leorolla on 2010-04-14
Good news!

Did you test with the ALSA daily build?

---

### Post by Riot@ct on 2010-04-14
> **leorolla said:**
> Good news!

Did you test with the ALSA daily build?
No, I have not still tried with the ALSA daily build.

---

### Post by msrinath80 on 2010-04-16
Any updates guys? Does the latest Lucid build have the audio fix??

---

### Post by prabashbala on 2010-04-16
I have the same Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] in my sony viao vpceb1e0e laptop. I have been trying to fix this sound error for weeks on ubuntu lucid 10.04 Beta.When i use a earphone i can hear a very weak sound .

I have the same problem but I think there,s no fix  for this bug yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532021](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532021)

anything new??

---

### Post by Riot@ct on 2010-04-17
I report a reply of a user from Launchpad:
The bug is fixed is in alsa-driver-1.0.23 release, so we just have to wait for it to get updated [http://packages.ubuntu.com/lucid/alsa-base](http://packages.ubuntu.com/lucid/alsa-base)
Daily sapshot alsa-driver-20100415.tar.gz from Takashi Iwai worked for me.
:popcorn:

---

### Post by msrinath80 on 2010-04-17
Thanks Riot@ct!

---

### Post by fabioa1978 on 2010-12-04
Hello All,

I need help. I am new to Linux and I just installed Linux on Sony Vaio VPCEB13FX. Everything is working good. Can you guys help me? What to do? the only thing not working is the Sound. Please help.

Thanks

---

