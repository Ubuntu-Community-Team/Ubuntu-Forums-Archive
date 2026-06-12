---
title: "Ubuntu Feisty and Presario V3000 Sound Problem"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by dreadlessdream on 2007-05-09
Hello all in the community...

ive got this problem since 2 days ago... i keep on try to google it but it seems still no solution for me.as a newbie i hope u can help me with my problem

i have Compaq presario with mcp51 and connexant.FYI since i install there is no sound come out from my speaker but my driver working good.This is the information script that i attach.Might be helpful

################################
ALSA Information Script v 0.4.23
################################


Linux Distribution
------------------

Ubuntu 7.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 7.04"


Kernel Information
------------------

Kernel release:    2.6.20-15-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


ALSA Version
------------

Driver version:     1.0.14rc4
Library version:    1.0.14rc4
Utilities version:  1.0.14rc4


Loaded ALSA modules
-------------------

snd_hda_intel


Soundcards recognised by ALSA
-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 22


PCI Soundcards installed in the system
--------------------------------------

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


Advanced information - PCI Vendor/Device/Susbsystem ID's
--------------------------------------------------------

00:10.1 0403: 10de:026c (rev a2)
	Subsystem: 103c:30b5


HDA-Intel Codec information
---------------------------

Codec: Conexant CX20549 (Venice)
Address: 0
Vendor Id: 0x14f15045
Subsystem Id: 0x103c30b5
Revision Id: 0x100100
Default PCM:
    rates [0x140]: 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x10 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x2a 0x2a]
  Pincap 0x0810014: OUT EAPD Detect
  Pin Default 0x95170110: [Fixed] Speaker at Int Top
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x2a 0x2a]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x2b 0x2b]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x62a1902e: [N/A] Mic at Sep Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x21451130: [Jack] SPDIF Out at Sep Rear
    Conn = Optical, Color = Black
  Pin-ctls: 0x00:
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x081124: IN Detect
  Pin Default 0x97a701f0: [Fixed] Mic at Int Riser
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x24: IN
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x54330121: [N/A] CD at Int Right
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x00:
Node 0x16 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x06]
Node 0x17 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x14, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-In vals:  [0x94 0x94] [0x94 0x94] [0x94 0x94] [0x94 0x94] [0x94 0x94]
  Power: 0x0
  Connection: 5
     0x19 0x14 0x12 0x11 0x15
Node 0x18 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x40]: 48000
    bits [0x6]: 16 20
    formats [0x5]: PCM AC3
Node 0x19 [Audio Output] wcaps 0xc11: Stereo
  PCM:
    rates [0x540]: 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: 0x0
Node 0x1a [Audio Input] wcaps 0x100d0b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x17, stepsize=0x05, mute=1
  Amp-In vals:  [0x17 0x17] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Power: 0x0
  Connection: 5
     0x17 0x14* 0x12 0x11 0x15
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono


ALSA Device nodes
-----------------

crw-rw---- 1 root audio 116,  0 2007-05-10 01:37 /dev/snd/controlC0
crw-rw---- 1 root audio 116, 24 2007-05-10 01:37 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 16 2007-05-10 01:37 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 17 2007-05-10 01:37 /dev/snd/pcmC0D1p
crw-rw---- 1 root audio 116,  1 2007-05-10 01:37 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 2007-05-10 01:37 /dev/snd/timer


Aplay output
------------

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Amixer output
-------------

-------Mixer controls for card 0 [NVidia]

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43
  Mono:
  Front Left: Playback 42 [98%] [on]
  Front Right: Playback 42 [98%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'LineIn',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Ext Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 23
  Front Left: 23 [100%] [34.50dB] Playback [on]
  Front Right: 23 [100%] [34.50dB] Playback [on]
Simple mixer control 'Int Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 23
  Front Left: 23 [100%] [34.50dB] Playback [on]
  Front Right: 23 [100%] [34.50dB] Playback [on]
Simple mixer control 'IntMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]


All Loaded Modules
------------------

Module
binfmt_misc
rfcomm
l2cap
bluetooth
ppdev
powernow_k8
cpufreq_ondemand
cpufreq_powersave
cpufreq_userspace
cpufreq_stats
freq_table
cpufreq_conservative
tc1100_wmi
pcc_acpi
sony_acpi
dev_acpi
button
dock
video
battery
sbs
i2c_ec
asus_acpi
backlight
container
ac
af_packet
parport_pc
lp
parport
fuse
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_oss
snd_seq_midi_event
joydev
bcm43xx
ieee80211softmac
snd_seq
snd_timer
snd_seq_device
ieee80211
ieee80211_crypt
nvidia
serio_raw
k8temp
snd
soundcore
snd_page_alloc
shpchp
pci_hotplug
pcspkr
i2c_nforce2
psmouse
agpgart
i2c_core
tsdev
evdev
ipv6
ext3
jbd
mbcache
sg
sd_mod
ide_cd
cdrom
usbhid
hid
sata_nv
ohci_hcd
ata_generic
ehci_hcd
usbcore
libata
scsi_mod
forcedeth
amd74xx
generic
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
vesafb
capability
commoncap

---

### Post by cool_reed on 2007-05-12
hi there.....

I have a Compaq V3149 AU . An Nvidia Geforce Go 6150 Card and Nvidia HD Audio.

With 6.10 I do not seem to have any problems with my sound it works perfectly. But with 7.4 the sound doesn't seem to come out at all..I have read through all the forums and don't seem to find a solution whatever i do. I followed many threads in this forum regarding this without luck. I have seen that many users of this model of compaq face similar problems, i do not know if this is a bug but hope someone out there can find a solution soon. Can someone be of help?

Thank you all for everything you are about to do.

Regards

Kishore

---

### Post by windedge on 2007-05-17
try this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392/comments/21]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392/comments/21")
it may be helpful

---

