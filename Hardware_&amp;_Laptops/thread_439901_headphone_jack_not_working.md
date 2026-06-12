---
title: "headphone jack not working"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by ramiro on 2007-05-11
I've got Ubuntu Feisty installed on on my Samsung M50 laptop. It's got Intel HDA Audio and the laptop speakers work perfectly fine. It also comes with a dock, and the headphone jack on the dock work perfectly fine as well.

However, the headphone jack on the actual laptop itself produces no noise when running ubuntu. If I plug something into it, sound stops coming out of the laptop speakers, but no sound comes out of the headphone jack

anyone got any ideas how to get sound working?

---

### Post by ramiro on 2007-05-17
here's my lspci:

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
06:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
06:07.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
06:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
06:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
06:09.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
06:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
06:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 03)


lsmod | grep snd
> snd_hda_intel          20504  1 
snd_hda_codec         204544  1 snd_hda_intel
snd_pcm_oss            43264  0 
snd_mixer_oss          16512  1 snd_pcm_oss
snd_pcm                76680  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_seq_midi            8576  0 
snd_rawmidi            24448  1 snd_seq_midi
snd_seq_midi_event      7424  2 snd_seq_oss,snd_seq_midi
snd_seq                49648  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    51716  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc          9992  2 snd_hda_intel,snd_pcm


---

### Post by metcalfe on 2007-11-18
hey, i have the same problem, 
all sound plays fine through the built in speakers of my laptop, but when i plug the headphones, sound stops on the speakers but doesn't play on the headphones.

i've unmuted everything on alsamixer and volume control but still no sound from the headphones, really annoying.

any ideas?

PS - i have an asus a6vm, lspci returns
> 00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

in case it helps:)
any tip would be greatly appreciated

---

