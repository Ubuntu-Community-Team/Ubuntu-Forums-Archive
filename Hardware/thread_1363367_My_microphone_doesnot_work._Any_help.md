---
title: "My microphone doesnot work. Any help?"
date: 2009-12-24
forum: Hardware
---

### Post by miros84 on 2009-12-24
Hello
I have Ubuntu 9.10
I have sound working well, but my microphone, doesnot work. I tried to record some voice and doesnot work. In windows, it works well.
Any idea how to make my microphon working?

---

### Post by miros84 on 2009-12-24
Here are some more information about my system:

Here are details for my sound card
Sound Blaster X-Fi Xtreme Audio
PCI\VEN_1102&DEV_0007&SUBSYS_10121102&REV_00\4&2966AB86&0&10A4

As I can see here, it is supporeted
[http://www.alsa-project.org/main/ind...-Creative_Labs](http://www.alsa-project.org/main/ind...-Creative_Labs)

```
uname -r
2.6.31-16-generic

```

```
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon Xpress 200 Host Bridge [1002:5a33] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200] [1002:5a61]
02:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
02:02.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```

```
dpkg -l | grep alsa
ii  alsa-base                                  1.0.20+dfsg-1ubuntu5                       ALSA driver configuration files
ii  alsa-utils                                 1.0.20-2ubuntu6                            ALSA utilities
ii  bluez-alsa                                 4.51-0ubuntu2                              Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.25-2ubuntu1.2                         GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-5                                   Enlightened Sound Daemon (ALSA) - Shared lib
ii  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                            Simple DirectMedia Layer (with X11 and ALSA 

```

```
lsmod | grep snd
snd_ca0106             34240  3 
snd_ac97_codec        101216  1 snd_ca0106
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_ca0106,snd_pcm

```

As I see here, my sound card is supported:[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

[[IMG]http://img689.imageshack.us/img689/6092/alsamixer.th.png[/IMG]](http://img689.imageshack.us/i/alsamixer.png/)

[[IMG]http://img405.imageshack.us/img405/4443/preferenssound.th.png[/IMG]](http://img405.imageshack.us/i/preferenssound.png/)

I tried analog input and analog microphone.
Nothing work

---

