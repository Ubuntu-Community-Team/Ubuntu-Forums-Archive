---
title: "No WiFi for Fujitsu Siemens Amilo li1818"
date: 2012-06-03
forum: Hardware
---

### Post by Ianman on 2012-06-03
Hi everyone,

I have been Googling my butt off but have not been able to find a solution to my problem yet.

I have a Fujitsu Siemens Amilo li1818 laptop and I simply cannot get WiFi running. The adapter has a hardware based switch which is set to ON. There are no settings in the BIOS to enable/disable it. 

if I type iwconfig I get this

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

So I am guessing it is not being detected at all. I am a bit of an Ubuntu n00b (still!!) but if anyone would mind trying to help I would greatly appreciate it!

Thanks!

---

### Post by josephmills on 2012-06-03
Hello there could you please open your terminal and enter in 
```
lspci -nn && lsmod 
``` Then paste that here ?  Thanks

---

### Post by Ianman on 2012-06-03
Here is the output (no idea what I just did LOL)

```
lspci -nn && lsmod
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
06:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_codec_si3054    12864  1 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_hda_intel          32765  6 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
psmouse                72919  0 
serio_raw              13027  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414672  4 
drm_kms_helper         45466  1 i915
drm                   197692  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd                    62064  20 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
video                  19068  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
fsam7400               13265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 26759  0
```

---

### Post by josephmills on 2012-06-03
umm I am not seeing a wireless card .. Is this a usb :) 
if so 
in terminal 
```
lsusb
```

and also 
```
sudo lshw -C network
```

then paste here thanks

---

### Post by Ianman on 2012-06-03
Nope definitely an internal wifi adapter. The laptop previously had Windows (IEUW!!!) and wireless worked fine.

I also see an indicator light that is on with a switch to turn wifi on and off. Here is a link to the [specs]("http://www.myce.com/notebooks-laptops/Fujitsu-Amilo-Li-1818-23408/specs/"). Unfortunately it does not show which adapter it is :(

---

