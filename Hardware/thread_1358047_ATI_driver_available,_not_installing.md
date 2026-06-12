---
title: "ATI driver available, not installing"
date: 2009-12-17
forum: Hardware
---

### Post by gradysghost on 2009-12-17
I just installed Ubuntu Karmic on my new Acer 5534-1121 laptop.  According to lspci, I have an Atheros AR928X wireless card.  I have an ATI Radeon 3200 HD video card.

So when I did the initial install, the ATI driver from the Hardware Drivers app installed and worked.  But I was missing wireless drivers, so I didn't even try to set up Compiz, opting instead to fix my wireless problem.

So I installed linux-backports-modules-karmic.  Rebooted.  Wireless worked!  Flawless!

Only now my ATI driver appears to have broken.  There is obvious screen-tearing when I move windows or switch to another desktop.  You can actually see the display being redrawn line-for-line, and it's really annoying.

So I opened up Hardware Drivers again.  It shows the "ATI/AMD proprietary FGLRX graphics driver" as not being activated.  I select it and click Activate.  I authenticate, then get the "Downloading and installing driver" window for all of 1.5 seconds.  That window disappears, returning me to Hardware Drivers.  The driver is still not activated.

I have used Synaptic to manually remove the ATI driver packages, and still have the same problem.  I have then reinstalled those driver packages through Synaptic to no great effect.

I uninstalled linux-backports-modules-karmic and expected wireless to quit working.  It did not quit working.  I am still connected to the Internet and posting this via my wireless network on the laptop in question.

Here is the output of lspci:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

And here is lsmod:

```
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
snd_hda_codec_realtek   203328  1 
arc4                    1660  2 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
ecb                     2524  2 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
ath9k                 307384  0 
mac80211              210408  1 ath9k
ath                     8444  1 ath9k
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
dm_crypt               12928  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56500  0 
serio_raw               5280  0 
k8temp                  4188  0 
cfg80211              130440  3 ath9k,mac80211,ath
led_class               4096  1 ath9k
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
shpchp                 32272  0 
i2c_piix4               9932  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
r8169                  32064  0 
mii                     5212  1 r8169
video                  19380  0 
output                  2780  1 video
```

I think it's important to note that the video problem didn't begin until after the installation of the backports package.  Any help you can provide would go a long way, I'm sure.

Thanks in advance,

Ryan


= = = = =
Mörgæs 2013-12-05:
Using Lubuntu 13.10 and the default open source drivers everything works in first attempt.

---

### Post by n0glu3 on 2009-12-17
Have you tried the driver from ATI's site?

---

### Post by gradysghost on 2009-12-17
As a matter of fact, I have.  I guess I should have mentioned that.  It had no effect as well, and I'm also concerned it may have made alterations to files like /etc/modules or something, and that may be part of the current problem.

I'm less than familiar with driver module handling in Linux.  Any idea of what I should check with that?

---

### Post by n0glu3 on 2009-12-17
I stopped using ATI ages ago because of the endless problems with the drivers. Unless you're going to play OpenGL 2.1+ games, I would use the open source drivers. They're a million times better except for hardcore 3D stuff.

---

### Post by gradysghost on 2009-12-18
That doesn't really help solve the problem because no drivers seem to be working here, open source or proprietary.  I will do a reinstall of the OS today to clear out any bad things I may have inadvertently done, and will try again.

---

### Post by spiperman on 2009-12-20
I'll just add a "me too" on this one.  I've been lurking since I upgraded to Karmic to see if there is a solution to this.  My ATI Radeon 9600 card has not worked since the upgrade  My lspci follows:

Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

I'll go back to watching now...

---

### Post by shebaw on 2010-03-25
Ya same here, ATi HD4570 and the same wireless card, Installed the linux backport packages and it broke my graphics card :(

---

### Post by shebaw on 2010-03-25
For all of you who are having this problem, here is the fix
[http://swiss.ubuntuforums.org/showthread.php?t=1438064&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1438064&page=2)

---

### Post by Yellow Pasque on 2010-03-25
For cleaning the proprietary drivers off the system and getting the open-source ATI driver to do 3D effects, here is a good Howto: [https://help.ubuntu.com/community/RadeonHD#Preparation](https://help.ubuntu.com/community/RadeonHD#Preparation)
Running the newer kernel mightfix wireless problems as well.

---

