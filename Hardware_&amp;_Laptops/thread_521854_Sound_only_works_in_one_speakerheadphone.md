---
title: "Sound only works in one speaker/headphone"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by Changturkey on 2007-08-09
I have a Lenovo C100, Intel GMA 915 Chipset, and the Realtek Ac'97 codec...

Heres some info..

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
Subsystem: Lenovo Unknown device 2061
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04) (prog-if 00 [VGA])
Subsystem: Lenovo Unknown device 2062
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
I/O ports at e000 [size=8]
Memory at a0000000 (32-bit, prefetchable) [size=256M]
Memory at d0080000 (32-bit, non-prefetchable) [size=256K]
Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
Subsystem: Lenovo Unknown device 2062
Flags: bus master, fast devsel, latency 0
Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
Subsystem: Lenovo Unknown device 206b
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at 1200 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
Subsystem: Lenovo Unknown device 206c
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at 1220 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
Subsystem: Lenovo Unknown device 206d
Flags: bus master, medium devsel, latency 0, IRQ 20
I/O ports at 1240 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
Subsystem: Lenovo Unknown device 206e
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at 1260 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
Subsystem: Lenovo Unknown device 206f
Flags: bus master, medium devsel, latency 0, IRQ 18
Memory at 40000000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=03, sec-latency=32
I/O behind bridge: 0000c000-0000dfff
Memory behind bridge: c0000000-cfffffff
Prefetchable memory behind bridge: 0000000090000000-000000009fffffff
Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
Subsystem: Lenovo Unknown device 2066
Flags: bus master, medium devsel, latency 0, IRQ 22
I/O ports at e100 [size=256]
I/O ports at e200 [size=64]
Memory at d00c0000 (32-bit, non-prefetchable) [size=512]
Memory at d00c0200 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
Subsystem: Lenovo Unknown device 207c
Flags: medium devsel, IRQ 17
I/O ports at e300 [size=256]
I/O ports at e400 [size=128]
Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
Subsystem: Lenovo Unknown device 2071
Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
Subsystem: Lenovo Unknown device 207b
Flags: bus master, medium devsel, latency 0, IRQ 20
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at 1100 [size=16]

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
Subsystem: Lenovo Unknown device 2073
Flags: medium devsel, IRQ 3
I/O ports at 1400 [size=32]

01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
Subsystem: Lenovo Unknown device 2076
Flags: bus master, medium devsel, latency 128, IRQ 17
Memory at c0004800 (32-bit, non-prefetchable) [size=2K]
I/O ports at c100 [size=128]
Capabilities: <access denied>

01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Subsystem: COMPAL Electronics Inc Unknown device 0012
Flags: bus master, medium devsel, latency 128, IRQ 21
I/O ports at c000 [size=256]
Memory at c0004000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

01:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
Subsystem: Broadcom Corporation Unknown device 044a
Flags: bus master, fast devsel, latency 128, IRQ 23
Memory at c0002000 (32-bit, non-prefetchable) [size=8K]

01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
Subsystem: Lenovo Unknown device 2075
Flags: bus master, medium devsel, latency 168, IRQ 16
Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=01, secondary=02, subordinate=02, sec-latency=176
Memory window 0: 90000000-93fff000 (prefetchable)
Memory window 1: c4000000-c7fff000
I/O window 0: 0000c400-0000c4ff
I/O window 1: 0000c800-0000c8ff
16-bit legacy interface ports at 0001

01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
Subsystem: Lenovo Unknown device 2079
Flags: bus master, medium devsel, latency 128, IRQ 5
Memory at c0000000 (32-bit, non-prefetchable) [size=128]
Capabilities: <access denied>

01:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
Subsystem: Lenovo Unknown device 2077
Flags: bus master, medium devsel, latency 128, IRQ 22
Memory at c0000100 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

01:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
Subsystem: Lenovo Unknown device 2078
Flags: bus master, medium devsel, latency 128, IRQ 5
Memory at c0000200 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

------------------------------------------------------------------------------------------------------------------

Size Used by
usbhid 26592 0
hid 27392 1 usbhid
binfmt_misc 12680 1
rfcomm 40856 0
l2cap 25856 5 rfcomm
bluetooth 55908 4 rfcomm,l2cap
ppdev 10116 0
i915 24448 2
drm 81044 3 i915
cpufreq_ondemand 9228 0
cpufreq_conservative 8200 0
cpufreq_powersave 2688 0
cpufreq_stats 7360 0
freq_table 5792 2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace 5408 0
sony_acpi 6284 0
tc1100_wmi 8068 0
dev_acpi 12292 0
pcc_acpi 13184 0
button 8720 0
dock 10268 0
sbs 15652 0
asus_acpi 17308 0
backlight 7040 1 asus_acpi
battery 10756 0
i2c_ec 6016 1 sbs
i2c_core 22656 1 i2c_ec
container 5248 0
ac 6020 0
video 16388 0
ipv6 268960 8
sbp2 23812 0
parport_pc 36388 0
lp 12452 0
parport 36936 3 ppdev,parport_pc,lp
fuse 46612 0
joydev 10816 0
snd_intel8x0 34332 2
snd_ac97_codec 98464 1 snd_intel8x0
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44544 0
snd_mixer_oss 17408 1 snd_pcm_oss
snd_pcm 79876 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 32896 0
snd_seq_midi 9600 0
snd_rawmidi 25472 1 snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
snd_seq 52592 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
serio_raw 7940 0
snd_timer 23684 2 snd_pcm,snd_seq
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
bcm43xx 126824 0
sdhci 18700 0
pcmcia 39212 0
ieee80211softmac 31360 1 bcm43xx
ieee80211 34760 2 bcm43xx,ieee80211softmac
psmouse 38920 0
snd 54020 14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti mer,snd_seq_device
soundcore 8672 1 snd
mmc_core 26756 1 sdhci
intel_agp 25244 1
snd_page_alloc 10888 2 snd_intel8x0,snd_pcm
ieee80211_crypt 7040 1 ieee80211
yenta_socket 27532 1
rsrc_nonstatic 14080 1 yenta_socket
pcmcia_core 40852 3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt 11812 0
iTCO_vendor_support 4868 1 iTCO_wdt
agpgart 35400 3 drm,intel_agp
af_packet 23816 4
evdev 11008 4
tsdev 8768 0
ext3 133128 1
jbd 59816 1 ext3
mbcache 9604 1 ext3
sg 36252 0
sr_mod 17060 0
cdrom 37664 1 sr_mod
sd_mod 23428 3
8139cp 25088 0
ata_generic 9092 0
ata_piix 15492 2
libata 125720 2 ata_generic,ata_piix
scsi_mod 142348 5 sbp2,sg,sr_mod,sd_mod,libata
8139too 27648 0
mii 6528 2 8139cp,8139too
ohci1394 36528 0
ieee1394 299448 2 sbp2,ohci1394
generic 5124 0 [permanent]
ehci_hcd 34188 0
uhci_hcd 25360 0
usbcore 134280 4 usbhid,ehci_hcd,uhci_hcd
thermal 14856 0
processor 31048 1 thermal
fan 5636 0
fbcon 42656 0
tileblit 3584 1 fbcon
font 9216 1 fbcon
bitblit 6912 1 fbcon
softcursor 3200 1 bitblit
vesafb 9220 0
capability 5896 0
commoncap 8192 1 capability
Changturkey is online now Report Post   	Reply With Quote

---

### Post by teachop on 2007-08-09
Hey that happens sometimes on my Acer laptop with Feisty.  It has Realtek audio too.

When it happens I have to run the volume all the way down with the function keys, and then run it back up, and it works out both speakers again.

---

### Post by fredj on 2007-08-10
Get the name of your soundchip by opening a terminal and typing
sudo cat /proc/asound/card0/codec\#*
The first line of output from that should give you the name of your soundchip. However if that
command doesn't work on your system you will have to look inside the /proc/asound dir and
its subdirectories to get the name of the soundchip.
Then do a search for that soundchip on these forums to see if there is a line you can add
to the /etc/modprobe.d/alsa-base file that will make your sound function correctly.
Also open the Alsa mixer (double click on the speaker icon) and add all the possible volume
controls and switches for both record and playback. Make sure they are all unmuted and that
volume levels are set.
Then from the System item on the taskbar goto Preferences->Sound and check that Alsa is
selected. Then click on the sound tab and make sure that the boxes at the top are selected.
In any program that you use to play sound make sure that it is looking at the correct device.
Most systems have at least two, the sound device and the modem device.

---

### Post by Changturkey on 2007-08-10
Both speakers give out sound, but the left side only gives out static. I checked my sound preferences and it is set to Alsa, everything is checked, I just don't know how to get to the /proc directory you mentioned, and my terminal replies that no such file or directory exists.

---

### Post by fredj on 2007-08-10
Yes the whistle is often only on one channel. To get to the correct directory open a terminal and
type cd /proc/asound then use the ls command to list the sub directories in asound.
We still need to know the name of your sound chip before we can help you.

---

### Post by Changturkey on 2007-08-11
All I got was this when I typed in ls

card0  cards  devices  ICH6  modules  oss  pcm  seq  timers  version

---

### Post by Changturkey on 2007-08-13
Is there anything else I need to type in?

---

### Post by fredj on 2007-08-13
No I don't think its worth your while typing anything else in.
Open the Alsa mixer (double click on the speaker icon in the taskbar). Go to the
File->Change Device menu and post a list of everything that appears under that menu.

---

### Post by Changturkey on 2007-08-14
Intel ICH6 (ALSA Mixer)

RealTek ALC250 rev 2 (OSS Mixer)

---

### Post by fredj on 2007-08-15
O.K your sound chip is a Realtek ALC250 rev 2. I can't find any common fixes for problems
with this but try opening the Alsa mixer (double click on the speaker icon). Then use the Edit->
Preferences Menu to add all the possible volume controls and switches for both playback and
record. Setting suitable volume levels on these might help.
You can also try editing the alsa-base file which is located in the /etc/modprobe.d directory.
Add a line to the bottom of the file as follows.
options snd-hda-intel position_fix=1 model=3stack
After saving the file reboot and see it if makes any difference, if not you can always remove it
again.

---

