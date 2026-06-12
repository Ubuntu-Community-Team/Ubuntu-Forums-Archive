---
title: "No sound after upgrade to Edgy (hda intel ALC 260)"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by kozimodo on 2006-10-27
I upgraded to Edgy using the alternative install CD yesterday and now I have no sound.  I also tried compiling the alsa-drivers to no avail.  The following are some of the usual diagnostics:
```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
06:03.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 20)
06:03.2 Class 0805: O2 Micro, Inc. Unknown device 7120
06:03.3 Bridge: O2 Micro, Inc. Unknown device 7130
06:05.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
06:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
```
```

$ lsmod|grep snd
snd_hda_intel          20500  1 
snd_hda_codec         168960  1 snd_hda_intel
snd_pcm_oss            47232  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84484  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              24964  1 snd_pcm
snd                    59908  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
```

Any ideas?

---

### Post by Jeff Gavett on 2006-10-27
I have Intel ICH6 and freaked that my sound was gone when I upgraded.

I just right clicked on the ALSA Mixer and checked, only to notice that the upgrade had, for some reason, simply muted everything except master volume on my computer. Hope this works for you, if not, sorry for assuming you're as silly as I am :p

---

### Post by hscottyh on 2006-10-27
Try muting your external speaker with alsamixer in a terminal.

---

