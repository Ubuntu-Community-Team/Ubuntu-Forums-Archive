---
title: "Problem between webcam and wireless card"
date: 2010-04-09
forum: Hardware
---

### Post by golamc on 2010-04-09
First of all sorry for my english....

My problem is simple...when i tray to use webcam (with cheese or emesene) or to test webcam with gstreamer properties my wireless card crash...To restor it normally i must remove battery of my laptop and replace it...But if i use webcam with guvcview or luvcview (From terminal) webcam start normally and wireless card not crash...WHY???

I have Ubuntu 9.10 (kernel 2.6.31-21)...my laptotp is Belinea o.book 2.1 with AMD dualcore TL-56...and that's from terminal:

**LSUSB**:
gabriele@gabriele-laptop:~$ lsusb
[COLOR=Red]Bus 001 Device 006: ID 04f2:b022 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 005: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter[/COLOR]
Bus 001 Device 003: ID 043e:70f1 LG Electronics USA, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0737 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
gabriele@gabriele-laptop:~$ 

**LSPCI:**
gabriele@gabriele-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
gabriele@gabriele-laptop:~$

[COLOR=Black]**LSMOD:**[/COLOR]
gabriele@gabriele-laptop:~$ lsmod
Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_codec_realtek   203328  1 
rt73usb                26336  0 
crc_itu_t               1852  1 rt73usb
snd_hda_codec_si3054     4636  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
rt2500usb              21152  0 
rt2x00usb              11548  2 rt73usb,rt2500usb
rt2x00lib              29756  3 rt73usb,rt2500usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
snd_pcm                75296  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
snd_seq_oss            28576  0 
x_tables               16544  1 ip_tables
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
cfg80211               93052  2 rt2x00lib,mac80211
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
btusb                  11856  2 
snd_seq                50224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                57332  0 
serio_raw               5280  0 
snd                    59204  18 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
k8temp                  4188  0 
shpchp                 32272  0 
i2c_piix4               9932  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
radeon                636000  2 
ttm                    36212  1 radeon
usb_storage            52768  1 
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
r8169                  32064  0 
mii                     5212  1 r8169
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp
video                  19380  0 
output                  2780  1 video
gabriele@gabriele-laptop:~$

THANX TO ALL

---

### Post by expos on 2010-06-06
Hi there,

I have the same problem here, with the same laptop Belinea o.book 2.1 by the way. I tried Kubuntu 9.10 and Kubuntu 10.04 as well as Opensuse 11.2 and the recent development version of 11.3, and Fedora 13. With all distributions it is the same problem. I wonder if there was a decline in one of the drivers as it worked before (until Opensuse 11.1).
I opened two bug reports for this:

Opensuse: [https://bugzilla.novell.com/show_bug.cgi?id=611976](https://bugzilla.novell.com/show_bug.cgi?id=611976)

Ubuntu: [https://bugs.launchpad.net/ubuntu/+bug/575000](https://bugs.launchpad.net/ubuntu/+bug/575000)

It would be nice if someone can help by telling how to go on with solving this problem, as I have no clue how to proceed.

I thought installing an old uvcvideo driver as it worked without problems with former releases. But I didn't find an old version in the internet.

So, any help is appreciated!

---

