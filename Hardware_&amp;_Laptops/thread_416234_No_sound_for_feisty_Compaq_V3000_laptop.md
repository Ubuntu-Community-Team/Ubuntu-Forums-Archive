---
title: "No sound for feisty Compaq V3000 laptop"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by lunatic on 2007-04-20
This is the first time i'm facing this kind of issue. Sound was quite ok for edgy but it didn't worked for feisty. There might be some other workaround. I've submitted a report on hardware database reporting the problem of sound. The model of laptop is Compaq V3000 series with Turion 64 and Nvidia graphics chipset.

Did any one faced the same problem? Please find the hardware database attached.

Thanks in Advance.

---

### Post by lunatic on 2007-04-21
I'm using Compaq V3133 series with AMd Turion64 and Nvidia chipset.

Pl. point me to some direction.

---

### Post by lunatic on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				More information on the hardware specs after running this script [http://www.linux-sound.info/alsa/index.php?task=support](http://www.linux-sound.info/alsa/index.php?task=support) 

The URL after running the scripts are

[http://pastebin.ca/450975](http://pastebin.ca/450975)
[http://pastebin.ca/450977](http://pastebin.ca/450977)
[http://pastebin.ca/450979](http://pastebin.ca/450979)
[http://pastebin.ca/450980](http://pastebin.ca/450980)

Thanks!

---

### Post by lunatic on 2007-04-21
################################
ALSA Information Script v 0.4.12
################################


Linux Distribution
------------------

DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 7.04"


Kernel Information
------------------

Kernel release:    2.6.20-15-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


ALSA Version
------------

Driver version:     1.0.14rc1
Library version:    
Utilities version:  1.0.13


Loaded ALSA modules
-------------------

snd_hda_intel


Soundcards recognised by ALSA
-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 17


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
  Amp-Out vals:  [0x28 0x28]
  Pincap 0x0810014: OUT EAPD Detect
  Pin Default 0x95170110: [Fixed] Speaker at Int Top
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x28 0x28]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x14 0x14]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x22a1902e: [Jack] Mic at Sep Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x01447130: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Yellow
  Pin-ctls: 0x00:
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x081124: IN Detect
  Pin Default 0x97a70120: [Fixed] Mic at Int Riser
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x24: IN
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x94330121: [Fixed] CD at Int Right
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
  Amp-Out vals:  [0x28 0x28]
  Pincap 0x0810014: OUT EAPD Detect
  Pin Default 0x95170110: [Fixed] Speaker at Int Top
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x28 0x28]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x14 0x14]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x22a1902e: [Jack] Mic at Sep Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x01447130: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Yellow
  Pin-ctls: 0x00:
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x081124: IN Detect
  Pin Default 0x97a70120: [Fixed] Mic at Int Riser
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x24: IN
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x94330121: [Fixed] CD at Int Right
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
  Amp-Out vals:  [0x28 0x28]
  Pincap 0x0810014: OUT EAPD Detect
  Pin Default 0x95170110: [Fixed] Speaker at Int Top
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x28 0x28]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x14 0x14]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x22a1902e: [Jack] Mic at Sep Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x01447130: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Yellow
  Pin-ctls: 0x00:
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x081124: IN Detect
  Pin Default 0x97a70120: [Fixed] Mic at Int Riser
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x24: IN
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x94330121: [Fixed] CD at Int Right
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

crw-rw---- 1 root audio 116, 7 2007-04-21 10:28 /dev/snd/controlC0
crw-rw---- 1 root audio 116, 6 2007-04-21 10:28 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 5 2007-04-21 10:28 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 4 2007-04-21 10:28 /dev/snd/pcmC0D1p
crw-rw---- 1 root audio 116, 3 2007-04-21 10:28 /dev/snd/seq
crw-rw---- 1 root audio 116, 2 2007-04-21 10:28 /dev/snd/timer


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

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43
  Mono:
  Front Left: Playback 40 [93%] [on]
  Front Right: Playback 40 [93%] [on]
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
  Front Left: 5 [22%] [7.50dB] Playback [on]
  Front Right: 5 [22%] [7.50dB] Playback [on]
Simple mixer control 'Int Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 23
  Front Left: 0 [0%] [0.00dB] Playback [on]
  Front Right: 0 [0%] [0.00dB] Playback [on]
Simple mixer control 'IntMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]


All Loaded Modules
------------------

Module
ipv6
binfmt_misc
rfcomm
l2cap
bluetooth
ppdev
powernow_k8
cpufreq_powersave
cpufreq_stats
cpufreq_ondemand
cpufreq_userspace
cpufreq_conservative
freq_table
sony_acpi
pcc_acpi
dev_acpi
tc1100_wmi
button
container
asus_acpi
dock
battery
ac
sbs
i2c_ec
video
backlight
sbp2
parport_pc
lp
parport
fuse
joydev
snd_hda_intel
snd_hda_codec
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
ide_cd
cdrom
snd_seq
snd_timer
snd_seq_device
bcm43xx
serio_raw
pcspkr
psmouse
sdhci
ieee80211softmac
snd
soundcore
mmc_core
snd_page_alloc
k8temp
ieee80211
ieee80211_crypt
i2c_nforce2
i2c_core
shpchp
pci_hotplug
af_packet
tsdev
evdev
ext3
jbd
mbcache
sg
sd_mod
amd74xx
generic
sata_nv
forcedeth
ohci_hcd
ohci1394
ieee1394
ata_generic
libata
scsi_mod
ehci_hcd
usbcore
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
vesafb
cfbcopyarea
cfbimgblt
cfbfillrect
capability
commoncap

---

### Post by constantine on 2007-04-21
hello there 

well i was just looking for the same problem that I had with my HP dv2000 . I have the same hardware 
and the same problem with sound ,though the sound was working at first installation .
Did you find any solution ?

Thanks

---

### Post by lunatic on 2007-04-21
Its working very cool just out of blue..i really wonder how it happened. Just hold on for a while it might heal in your case to. There is  script to reset all you audio devices. Try em.

[http://www.linux-sound.info/alsa/index.php?task=scripts](http://www.linux-sound.info/alsa/index.php?task=scripts)

---

### Post by godvalve on 2007-04-21
GRRRRR! What's with this! I install Edgy (Which was "just supposed to work") and networking support did not support my wireless. I install Feisty and now my sound (which worked out of the box in Edgy) no longer works. I have a Toshiba Sattelite A100 now without sound but working wireless. *wonderful*:mad:

By the way, the scripts are of no use in solving this issue. Thx for the suggestion though.

---

### Post by karhulitos on 2007-04-21
Me too. Dapper/Edgy ok, but Feisty no sound.
[http://pastebin.ca/451266](http://pastebin.ca/451266)

---

### Post by atek101 on 2007-04-23
I have a Presario V3000Z Turion-nVidia-Conexant combo, same problem. Sound occassionally works on some bootups and not others. No clue why.

---

### Post by erniequintero on 2007-04-23
after a did a ubuntu system update it fixed for me:)

---

### Post by iko1234 on 2007-04-23
I did a system update but it didnt fix it for me. :(  I can't get sound to work no matter what I try.

---

### Post by zxguitar on 2007-04-23
i have the same problem, i had the ubuntu 6.10 edgy, and it worked fine, but i use the live cd of feisty i i noted there was no sound, i try to configure, but i couldn't do nothing, so instead of install it, i upgraded it, you know, to keep the settings, but there's no sound, i don't understad, it's suppoused that a newer version of a sofware it is better than the previous at all, but i really don't understad why this is happening, well if anyone can help, THX :popcorn:

---

### Post by the lush on 2007-04-24
I am using an Asus laptop with Intel sound. The sound worked until I installed the Nvidia driver. With this in, when I start the system, there is sound, but the screen resolution is only 1024*768, when I go to the Nvidia settings to correct the resolution to 1400*900 I lose sound.

---

### Post by dracule on 2007-04-24
i had the problem when i dual booted into XP and muted it there, then the sound wouldnt work in ubuntu (i have the same laptop as you). when i unmuted in XP the sound came back in ubuntu.

also, with this laptop, when you plug in your headphones, the speakers still play (in ubuntu, in XP the speakers shut off so only the head phones are on) any ideas on how to fix this?

---

### Post by the lush on 2007-04-25
A chap or chapess by the name of Slade Winstone posted this [http://ubuntuforums.org/showthread.php?p=2529534#post2529534]("http://ubuntuforums.org/showthread.php?p=2529534#post2529534") I followed his instructions and now have no more sound problems. It involves adding one extra line to a file, and after that sound just works. Hope this helps.

Oh, to save you clicking, here is his/her post:

> Hi,

Upgraded my ASUS A8M Laptop to Feisty (7.04) and my sound stopped working.

nForce Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) = snd-hda-intel.

The following fixes the sound problem:

I added the following to the end of '/etc/modprobe.d/alsa-base' and restarted my computer:

Code:

# Added according to tips from launchpad.net.
options snd-hda-intel model=3stack

Thanks to the posts in the Feisty development threads.

Slade.

I am not using the same model of laptop, and do not have the same audio device, but it still worked for me.

---

### Post by aaron552 on 2007-04-25
I have a Compaq V3118AU laptop but adding that line didn't help, in fact the audio may be working less often now. :(

---

### Post by midjunkie on 2007-04-25
Same problem here, running on a Presario v3217LA with the nVidia+Conexant combo. Worked great on Edgy, but upgrading to Feisty just killed all sound. Adding extra lines to alsa-base didn't help me neither ;(

---

### Post by thejaunt on 2007-04-25
I have same problem no sound on my v3000. I have been looking everywhere for a solution. My sound was working fine on edgy 6.10 then I upgraded to feisty and the sound worked the first time a booted but now nothing. I tried the above method: 

sudo gedit /etc/modprobe.d/alsa-base

to no avail. It did nothing. Since the sound once worked I'm sure its a problem with something not being loaded every time I reboot the system. If I find a fix I will post I hope others will do the same.

Kindest Regards
TheJaunt

---

### Post by lazc on 2007-04-25
I have a HP 2310us has Turion X2-Nvidia-HD Audio hardware, has same issue, but I wonder if this is related with the issues with sleep on this hardware?

---

### Post by cmat on 2007-04-25
I have an Acer Aspire 5040. The sound worked great in 6.10, but failed in 7.04.

---

### Post by thejaunt on 2007-04-25
I found this documentation that is supposed to be a fix but I dont have time to try it I have to go to work maybe someone can check it out tell me how it goes. Heres the link

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Peace

---

### Post by tonywhelan on 2007-04-25
> **godvalve said:**
> GRRRRR! What's with this! I install Edgy (Which was "just supposed to work") and networking support did not support my wireless. I install Feisty and now my sound (which worked out of the box in Edgy) no longer works. I have a Toshiba Sattelite A100 now without sound but working wireless. *wonderful*:mad:

By the way, the scripts are of no use in solving this issue. Thx for the suggestion though.

Try this (worked fine on my Acer laptop):

In a terminal window I ran "alsamixer" which brings up a graphical mixer window. Alll my speaker values were set off ("MM").

 Used the cursor arrow to move to the desired 'column' and then pressed the "M" on keyboard to toggle that column on or off. MM is off, 00 is on. Then used up arrow to raise volume to desired level.

All ok.

---

### Post by dracule on 2007-04-26
gosh this is insane, my sound was working for 3 days, now it stopped. i followed the instructions linked but it didnt work.

v3000 like yours

---

### Post by thejaunt on 2007-04-26
tonywhelan: Thx But no workie. I ran alsamixer and already had all 00 all across the board. I even switched them from 00 to mm and then back to 00.
Thx though bro.

---

### Post by agnimidhun on 2007-04-26
Hi All,

   I too have a V3033 laptop with Nvidia card.. The sound was not working with Ubuntu 7.04. I gave up and then started to install other open source applications. The Desktop effects required I enable the restricted software support for Nvidia.. I did that and after the reboot. The sound was up!! I was rather surprised.. I dont know if this is exactly due to enabling the Restrcited Driver for Nvidia.. BUt may be u can try it.. 


Cheers!!!
Midhun.

---

### Post by thejaunt on 2007-04-26
agnimidhun: Could you be a bit more specific? What applications did you install ? How did you enable restricted software support for NVIDIA?

---

### Post by dracule on 2007-04-26
ok, this is weird, it is now working. i opened it up today and woola the sign in screen did the little beep thing. for somereason, the sound wont work for about a day and then BAM it works.

---

### Post by midjunkie on 2007-04-27
*bump* [-o<

---

### Post by cmat on 2007-04-27
my sound card on my laptop isn't even present. I have an ACER ASPIRE 5040 laptop and the sound card has been identified as SB.

---

### Post by dracule on 2007-04-28
OK, who is ever having this problem, do you dual boot? when i stick in linux it works. when i boot into windows, and then go to linux, it stops working... idk if this can be of any assistance.

---

### Post by thejaunt on 2007-04-28
I dual boot with vista and feisty but I have not noticed any change in sound. I dont think thats the problem.

---

### Post by reedatschool on 2007-04-29
V3000 SERIES COMPAQ PRESARIO
Just installed Feisty here and now my Sound and DVD player no longer work correctly.  Both worked correctly under Edgy.  DVD read is fine, but when I go to burn a DVD it errors out or doesn't do anything.

I have tied several solutions for the sound but nothing seems to work.  I have tried turning on DMA for DVD but it doesn't help.  Anyone found solutions to these yet?

---

### Post by ogifell on 2007-04-30
I was having the same problem, no sound on my V3000.  I installed ALSA v1.0.14 rc3.  I now have sound, BUT the headphone jack is doing something its never done before.  When I turn the computer on, the speakers work.  If I plug headphones in, I get sound through the headphones AND speakers.  Then, when I remove the headphones, the speakers shut off.  Its as if the switch in the headphone jack begins working in reverse.  When I restart the computer, everything works fine.

Any ideas?

---

### Post by dracule on 2007-04-30
> **ogifell said:**
> I was having the same problem, no sound on my V3000.  I installed ALSA v1.0.14 rc3.  I now have sound, BUT the headphone jack is doing something its never done before.  When I turn the computer on, the speakers work.  If I plug headphones in, I get sound through the headphones AND speakers.  Then, when I remove the headphones, the speakers shut off.  Its as if the switch in the headphone jack begins working in reverse.  When I restart the computer, everything works fine.

Any ideas?

mine works, if i mute and unmute. when i plug my head phones in i mute unmute, then the play through only the headphones. then when i unplug them, i mute unmute and speaker sound comes on.

---

### Post by reedatschool on 2007-05-01
> **reedatschool said:**
> V3000 SERIES COMPAQ PRESARIO
Just installed Feisty here and now my Sound and DVD player no longer work correctly.  Both worked correctly under Edgy.  DVD read is fine, but when I go to burn a DVD it errors out or doesn't do anything.

I have tied several solutions for the sound but nothing seems to work.  I have tried turning on DMA for DVD but it doesn't help.  Anyone found solutions to these yet?

UPDATE:

Tried installing OSS and also manually compiling ALSA and neither work.  DVD burner is working, I forgot I couldn't burn files over a certain size.

Read somewhere this has to do with the Nforce drivers in Linux being discontinued and the fact that  now we are relying on ALSA to provide support that still is in the experimental stages.  

I downgraded and re-installed Edgy today, tired of fiddling with the sound.  Hopefully someone can address this issue or find a workaround.
:confused:

---

### Post by kitsura on 2007-05-02
Finally got sound working for my V3063 laptop. What I did was open the volume control, umute PCM-2 and turned the volume up. Hopefully this will work for others who are having the same problem.

---

### Post by mbx118 on 2007-05-02
What has worked for me, so far at least  (4 boots in a row) is this website. [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)  I know everybody's seen this before, but i specify two options.

options snd-hda-intel model=ref
options snd-hda-intel model=m2-2

once again, can't guarantee anything but seems to work well over here.

---

### Post by fmercado on 2007-05-02
installing Alsa 14 worked just fine for me..

it takes only 5 minutes.. te headset jack now works..

greetings.

---

### Post by cmat on 2007-05-02
i've tried all of that. mine says that the mixer isn't detected. in other words my sound device. worked fine in edgy but not feisty. i'm going to put openSUSE on my laptop until this problem is fixed. ubuntu works great on my desktop so i'm keeping it there. :)

---

### Post by raulin on 2007-05-03
I'm in a HP dv2125 with Audio Device: nVidia Corporation MCP51 High Definition Audio (rev a2) running Feisty (dual boot with XP)

My problem is the same named above, sound works correctly when first boot in the morning, but it goes away on reboot

I have done everything suggested in this and other posts about this issue but couldn't make the sound work in my machine

This is what I have tried:

:mad: Adding the line:
```
options snd-hda-intel model=3stack
```
to /etc/modprobe.d/alsa-base with different endings (5stack, 6stack, laptop, laptop-eapd, m2-2, and ref)

:mad: Executing in terminal:
```
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=auto
```

:mad: And finally updating to the latest version of alsa:
alsa-driver (1.0.14rc3)
alsa-lib (1.0.14rc3)
alsa-utils (1.0.14rc2)


I'm still struggling with this PLEASE somebody help!!!!

I want to keep Feisty since it has been the only Ubuntu distro in which I could make my graphics 3D card with my Wireless card!!!

---

### Post by dev3 on 2007-05-03
hi to all.
I just tried out Linux with Ubuntu for the first time, and I had a problem with the sound, namely no sound.  I have a Compaq V3018TU.
I am a total Linux Noob, so I was worried.
I tried the instructions on [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
and now I have perfect sound on my Laptop speakers. ( I think it is better than on Windows XP)
The only problem I am now facing is crappy sound in my Headphones, when the volume is large.

---

### Post by theonlykman on 2007-05-08
Installing Feisty, everything worked fine out of the box. The only problem is that I have horrible quality through headphones. Other than that sound is great on my v3000. Does anyone else have working but crappy headphone issues?

---

### Post by cool_reed on 2007-05-09
I have similar problems.....

[http://pastebin.ca/479409](http://pastebin.ca/479409)

here there is a list of my sound configurations....similar to most other people...I cannot have my sound running again....dont know if this is a bug....any new updates?

---

### Post by windedge on 2007-05-17
found a work around: just shut down, disconnect power source, boot again.
it works for me, see following url:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392")

---

### Post by dutchcow on 2008-01-31
The problems here are the same found in [this]("http://ubuntuforums.org/showthread.php?t=239995") thread. Check out the last pages. I myself am running on a v3000 series notebook (v3010au) with the same nvidia chipset, sound has been fixed in the new (10.0.15) alsa drivers (the old ones caused the issues). Try upgrading to hardy or wait till they merge alsa 1.0.15 into the repo's for gutsy and feisty.

---

