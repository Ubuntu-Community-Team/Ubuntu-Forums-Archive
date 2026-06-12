---
title: "VMWare Workstation + Ubuntu 9.10 = no sound for either"
date: 2010-03-05
forum: Hardware
---

### Post by dtbravo on 2010-03-05
Hi All,
I recently installed [COLOR=Red]VMWare Workstation 7.0.0 build-203739[/COLOR], and I got that common error[COLOR=Black] "Cannot connect virtual sound device. No corresponding device on the host."[/COLOR][COLOR=Black][COLOR=#3366FF][/COLOR][/COLOR]  Or something like that.  I did some searching and found that this is a common problem.  The difference for me, is that now the sound on my host OS won't work, and I was listening to music prior to the install.  So now I have no sound, and I can't figure out why.  Maybe switch to ALSA?  Ideas?
-T

Relevant Info:

```
# uname -a
Linux centurion [COLOR=Red]2.6.31-19-generic[/COLOR] #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 [COLOR=Red]i686[/COLOR] GNU/Linux

```

```
$ sudo lspci
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
[COLOR=Red]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)[/COLOR]
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX+] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 RAID bus controller: Promise Technology, Inc. PDC42819 [FastTrak TX2650/TX4650]
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
```

```
$ sudo lsmod
Module                  Size  Used by
vmnet                  43004  13 
parport_pc             31940  0 
vmblock                12444  1 
vsock                  39904  0 
vmci                   54388  1 vsock
vmmon                  73100  0 
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
ppdev                   6688  0 
[COLOR=Red]snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  0 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss[/COLOR]
iptable_filter          3100  0 
[COLOR=Red]snd_seq_dummy           2656  0 [/COLOR]
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
[COLOR=Red]snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd[/COLOR]
[COLOR=Red]snd_page_alloc          9156  2 snd_hda_intel,snd_pcm[/COLOR]
i2c_piix4               9932  0 
lp                      8964  0 
parport                35340  3 parport_pc,ppdev,lp
nvidia               9586440  36 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
ohci1394               29900  0 
r8169                  32064  0 
ieee1394               86596  1 ohci1394
mii                     5212  1 r8169
floppy                 54916  0 
usbhid                 38208  0 
ati_agp                 6760  0 
agpgart                34988  2 nvidia,ati_agp
```

---

