---
title: "Just another HDA Intel Problem... Some help needed..."
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by prodrigues on 2006-10-26
Hi,

I'm new in this community, and I have been reading problems about HDA Intel.

After updating my system, suddenly I got no sound... And when I do lsmod, there's nothing with "snd" or "sound"...

When I do lspci it shows my card:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

When I try to install the Realtek alsa driver, It ends with errors... Even before I got no sound...

Any Idea?...

Thanks for any answers.

---

### Post by prodrigues on 2006-10-26
Compiled the alsa driver, lib and utils... but I still without sound... And without modules...

```
modprobe snd-hda-intel;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
FATAL: Module snd_hda_intel not found.
FATAL: Module snd_pcm_oss not found.
FATAL: Module snd_mixer_oss not found.
FATAL: Module snd_seq_oss not found.

```

Any idea?

---

### Post by sml on 2007-11-10
Same problem for me. I thought Ubuntu was a professional distribution.

---

### Post by sml on 2007-11-13
Maybe not :(

---

