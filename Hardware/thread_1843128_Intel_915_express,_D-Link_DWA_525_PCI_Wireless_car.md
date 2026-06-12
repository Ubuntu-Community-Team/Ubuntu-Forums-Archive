---
title: "Intel 915 express, D-Link DWA 525 PCI Wireless card - Can't see PCI devices"
date: 2011-09-12
forum: Hardware
---

### Post by ashesh0326 on 2011-09-12
Hi,
I recently purchased a brand new D-Link DWA 525 wireless network card for my old desktop running Ubuntu 11.04 with an Intel 915 motherboard. To my horror, I found that the card was still widely unsupported and D-Link's own drivers were in alpha.

That apart, I couldn't find this card when I did an lspci, or an lsmod for that sake. The system remains oblivious to this card.

My desktop has two PCI slots and I've tried pushing the card in both with similar results.

Any help would be greatly appreciated, otherwise it's money going down the toilet for me.

Here's the o/p from lspci:
```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

From lsmod
```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
i915                  450944  3 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40745  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  4 i915,drm_kms_helper
soundcore              12600  1 snd
ndiswrapper           188098  0 
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
video                  18951  1 i915
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
r8169                  42534  0 

```

Thanks.

---

