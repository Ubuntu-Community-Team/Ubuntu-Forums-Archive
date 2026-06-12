---
title: "Logitech Quick Cam Chat Not Working, No microphone either"
date: 2010-01-14
forum: Hardware
---

### Post by whoboo on 2010-01-14
What is the correct driver and how do I get it ?  Camera is crashing in Cheese.  Also microphone not recognized.
lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:092c Logitech, Inc. QuickCam Chat
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

uname -a
Linux householdone 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

 lsdev
Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:1f.0                 1000-107f 1180-11bf
0000:00:1f.1                 0170-0177 01f0-01f7 0376-0376 03f6-03f6 1800-180f
0000:00:1f.2                 1820-183f
0000:00:1f.3                 1810-181f
0000:01:0d.0                   3000-300f   3010-3013   3014-3017   3018-301f   3020-3027
0000:01:0e.0                   3400-34ff
ACPI                             1000-1003     1004-1005     1008-100b     1028-102b     102c-102f
ata_piix              14 15    0170-0177   01f0-01f7   0376-0376   03f6-03f6   1800-180f
cascade             4     2 
CS4281                   11 
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
eth0                     10 
floppy              2     6  03f2-03f2 03f4-03f5 03f7-03f7
fpu                          00f0-00ff
i8042                  1 12 
keyboard                     0060-0060 0064-0064
parport0                  7  0378-037a
pata_pdc2027x             9 
PCI                          0cf8-0cff 3000-3fff
pic1                         0020-0021
pic2                         00a0-00a1
pnp                          0290-0297 0400-0404 04d0-04d1   1000-107f   1180-11bf
rtc0                      8  0070-0071
serial                       03f8-03ff
timer                     0 
timer0                       0040-0043
timer1                       0050-0053
uhci_hcd                       1820-183f
vga+                         03c0-03df
via-rhine                        3400-34ff
XT-PIC-XT                 4 

 lsmod
Module                  Size  Used by
i810                   17788  2 
drm                   159584  3 i810
snd_cs4281             17184  3 
gameport               11368  2 snd_cs4281
snd_ac97_codec        101216  1 snd_cs4281
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  2 snd_pcm_oss
snd_pcm                75296  3 snd_cs4281,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9156  1 snd_pcm
snd_opl3_lib           10396  1 snd_cs4281
iptable_filter          3100  0 
snd_hwdep               7200  1 snd_opl3_lib
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
snd_seq_oss            28576  0 
x_tables               16544  1 ip_tables
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_cs4281,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_pcm,snd_opl3_lib,snd_seq
gspca_spca561           9372  0 
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gspca_main             22812  1 gspca_spca561
snd                    59204  16 snd_cs4281,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               36736  1 gspca_main
ppdev                   6688  0 
v4l1_compat            14496  1 videodev
soundcore               7264  2 snd
parport_pc             31940  1 
psmouse                56500  0 
lp                      8964  0 
intel_rng               4444  0 
shpchp                 32272  0 
serio_raw               5280  0 
parport                35340  3 ppdev,parport_pc,lp
via_rhine              22212  0 
mii                     5212  1 via_rhine
floppy                 54916  0 
intel_agp              27484  1 
agpgart                34988  3 drm,intel_agp


I would like to use this camera on skype and ekiga.

Cheese crash  cheese[3374]: segfault at 798 ip 00fff812 sp b4c8e1a0 error 4 in libglib-2.0.so.0.2200.3[fac000+b5000]

I previously tried to get a microsoft 3000vx to work on this machine, downloading and compiling and installing drivers in vain.  I expected the Logitech to work, out of the box, so to speak.

Help will be appreciated.

---

### Post by Tirish Anau on 2010-01-19
tirish@Tirish:~$ 1susb
No command '1susb' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
1susb: command not found
tirish@Tirish:~$ lsusb
Bus 002 Device 006: ID 04e8:6734 Samsung Electronics Co., Ltd 
Bus 002 Device 005: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 002 Device 004: ID 0a48:5014 I/O Interconnect Mass Storage Device
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:092e Logitech, Inc. QuickCam Chat
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

My problem is this......
It doesn't work in skype i've surfed the forums for a solution to no avail. I wondered if it was a driver problem and downloaded camorama and several other device managers again no avail. My question would be this why do i see a fuzzy green screen when i test in skype? My second question is there a program for video adjustment brightness the whole bit?

I'm running a 64 bit version of 9.10 and i have an amd triple core phenom

---

### Post by alejaaandro on 2010-01-19
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293176)

---

