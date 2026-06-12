---
title: "Zenbook UX533FAC - no sound at all"
date: 2020-05-20
forum: Hardware
---

### Post by wodkabylazaslona on 2020-05-20
0

                                         I've got a fresh install of Ubuntu 20.04 on UX533FAC. Unfortunately sound does not work at all. And I've got no single clue why.
  hwinfo

  ```
sudo hwinfo --sound
17: PCI 1f.3: 0403 Audio device                                 
  [Created at pci.386]
  Unique ID: nS1_.9G5mT1GK4nF
  SysFS ID: /devices/pci0000:00/0000:00:1f.3
  SysFS BusID: 0000:00:1f.3
  Hardware Class: sound
  Model: "Intel Audio device"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x02c8 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x1a61 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xb1218000-0xb121bfff (rw,non-prefetchable)
  Memory Range: 0xb1000000-0xb10fffff (rw,non-prefetchable)
  IRQ: 146 (746 events)
  Module Alias: "pci:v00008086d000002C8sv00001043sd00001A61bc04sc03i80"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Driver Info #1:
    Driver Status: snd_sof_pci is active
    Driver Activation Cmd: "modprobe snd_sof_pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```  And dmesg

  ```
dmesg | grep realtek
[    2.174184] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC294: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[    2.174186] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    2.174187] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    2.174188] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    2.174189] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    2.174190] snd_hda_codec_realtek hdaudioC0D0:      Headset Mic=0x19
[    2.174191] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12

```  Is there anything I can do to use Ubuntu on this notebook?

---

### Post by wodkabylazaslona on 2020-05-20
I found out:
[https://bbs.archlinux.org/viewtopic.php?id=255446&fbclid=IwAR1YfR4EWxEeHewpvtwNjDQSX2IJTglEtwwD3ETmB79efGaj9QFr3W_XXLE](https://bbs.archlinux.org/viewtopic.php?id=255446&fbclid=IwAR1YfR4EWxEeHewpvtwNjDQSX2IJTglEtwwD3ETmB79efGaj9QFr3W_XXLE)

It is probably the same issue, so I will have to rely on Windows :(.

---

### Post by Yellow Pasque on 2020-05-20
I see some similar complaints for Asus UX5 series, but I don't know if they're the exact same problem as your model:
[https://bugzilla.kernel.org/show_bug.cgi?id=206145](https://bugzilla.kernel.org/show_bug.cgi?id=206145)

---

