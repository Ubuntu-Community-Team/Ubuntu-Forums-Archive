---
title: "No XV on HP nx6110/Intel Mobile 915GM/PM/GMS/910GML Express"
date: 2011-06-15
forum: Hardware
---

### Post by moody_cz on 2011-06-15
Hello,

I'm using Lubuntu 11.04 and having problem with video playback, which is .. pretty slow, especially in fullscreen. I've realized it's due to the fact I don't have any XV port available. Xvinfo utility gives me this:

```

X-Video Extension version 2.2
screen #0
 no adaptors present

```

lspci output:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 Multimedia video controller: Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

When I try to run Xorg -configure, it fails on modprobing i915 module, when I try to do it manually, it says:

```

insmod /lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/i915/i915.ko 
FATAL: Error inserting i915 (/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/i915/i915.ko): No such device

```

Any ideas?

Thanks in advance.

---

### Post by moody_cz on 2011-08-28
Hello :)

I'm gonna give it one more try. I've managed to work DRI with i915 module on the very same laptop, just now after updates and reboot I've got the same problem again. 

```

FATAL: Error inserting i915 (/lib/modules/2.6.38-11-generic/kernel/drivers/gpu/drm/i915/i915.ko): No such device

```

And dmesg says:

```

[    0.376912] Linux agpgart interface v0.103
[    0.376994] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    0.377057] agpgart-intel 0000:00:00.0: detected gtt size: 0K total, 0K mappable
[    0.377066] agpgart-intel 0000:00:00.0: Intel (null) Chipset
[    0.377073] agpgart-intel 0000:00:00.0: can't determine aperture size
[    0.377076] agpgart-intel 0000:00:00.0: agp_backend_initialize() failed
[    0.377082] agpgart-intel: probe of 0000:00:00.0 failed with error -22
[    1.741637] [drm:i915_init] *ERROR* drm/i915 can't work without intel_agp module!

```

lsmod:

```

Module                  Size  Used by
snd_hrtimer            12680  1 
sha256_generic         20911  2 
parport_pc             32111  0 
ppdev                  12849  0 
cryptd                 19801  0 
aes_i586               16956  516 
aes_generic            38023  1 aes_i586
dm_crypt               22463  1 
vesafb                 13449  1 
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
joydev                 17322  0 
snd_seq_midi           13132  0 
pcmcia                 39671  0 
b43                   296610  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 13418  0 
yenta_socket           27230  0 
sparse_keymap          13666  1 hp_wmi
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
cfg80211              156212  2 b43,mac80211
snd                    55295  10 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
drm_kms_helper         40745  0 
drm                   184164  1 drm_kms_helper
b44                    35301  0 
ssb                    45942  2 b43,b44
i2c_algo_bit           13184  0 
video                  18951  0 

```

Kernel is configured with built-in intel_agp support. Any ideas?

Thanks in advance.

---

