---
title: "Mouse and keyboard laggy"
date: 2012-06-18
forum: Hardware
---

### Post by galapogos on 2012-06-18
I've just installed Ubuntu 10.04 LTS 64bi on my i5-2400 system, and I'm experiencing very laggy keyboard and mouse input.
  I have to type really slowly or I some keys will not get registered.  Also, the mouse cursor moves around very slowly at a very low frame  rate.
  I've checked my keyboard and mouse settings and they seem to be fine.  System monitor doesn't show any processes taking up significant CPU  utilization. What else could be wrong?

---

### Post by Hari Babu on 2012-06-18
Restart the system once ....


:guitar:

---

### Post by galapogos on 2012-06-18
That doesn't work. The problem actually starts occurring even upon booting the Live CD, so it's probably a driver issue?

---

### Post by typhoon_tip on 2012-06-18
> **galapogos said:**
> That doesn't work. The problem actually starts occurring even upon booting the Live CD, so it's probably a driver issue?

Have you done all the updates in your installed copy of 10.04 ?

Anyway yes, could very well be a driver issue. Try out the live CD for 12.04, and see if the issue is still there or not (newer Kernel, newer Firmware package !).

---

### Post by galapogos on 2012-06-19
I've tried 12.04 before this, however it was the 32bit version. It worked just fine. The problem is that I have to use 10.04 LTS since something I'm doing isn't supported in 12.04.

Is there any way of backporting the chipset/USB drivers like how it was done with the intel graphics drivers?

Just fyi, here's output from lspci -knn

```

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0100] (rev 09)
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0102] (rev 09)
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:16.3 Serial controller [0700]: Intel Corporation Cougar Point KT Controller [8086:1c3d] (rev 04)
    Kernel driver in use: serial
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 5 [8086:1c18] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.6 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 7 [8086:1c1c] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.7 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 8 [8086:1c1e] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a4)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c4c] (rev 04)
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c02] (rev 04)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
    Kernel modules: i2c-i801

```
Here's output from lsmod:

```

Module                  Size  Used by
rndis_host             13801  0 
cdc_ether              13201  1 rndis_host
usbnet                 26147  2 rndis_host,cdc_ether
snd_hda_codec_hdmi     28012  1 
snd_hda_codec_realtek   336223  1 
binfmt_misc            17498  1 
ppdev                  17180  0 
usb_storage            57483  0 
uas                    17891  0 
tpm_infineon           17403  0 
snd_hda_intel          32995  2 
snd_hda_codec         103312  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13652  1 snd_hda_codec
snd_pcm                96468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30385  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61538  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29708  2 snd_pcm,snd_seq
snd_seq_device         14490  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67573  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  518754  3 
soundcore              12680  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
drm_kms_helper         42312  1 i915
usbhid                 46708  0 
psmouse                73514  0 
lp                     17789  0 
drm                   227591  4 i915,drm_kms_helper
hp_wmi                 13683  0 
serio_raw              13208  0 
hid                    94906  1 usbhid
sparse_keymap          13890  1 hp_wmi
i2c_algo_bit           13368  1 i915
parport                46360  2 ppdev,lp
video                  19465  1 i915
tpm_tis                18502  0 
tpm                    22259  2 tpm_infineon,tpm_tis
tpm_bios               13676  1 tpm
ahci                   26002  2 
libahci                30664  1 ahci
e1000e                158424  0 

```

Here's output from lsusb:

```

Bus 002 Device 004: ID 1a74:6356  
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 001 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by typhoon_tip on 2012-06-19
Have you fully updated your installed copy of 10.04 ?

However, if you need to stick to 10.04 for Gnome 2 reasons, you can give 10.10 and 11.04 a try as well.

---

