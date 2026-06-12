---
title: "gutsy: intel ich8 no sound...."
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by ffi on 2008-02-11
i have read the threads and multitude of bug reports but still am not able to enable sound, i have enabled backports

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.15 (Tue Oct 16 14:57:44 2007 UTC).

the module seems to load:

$ lsmod | grep intel
snd_hda_intel         296480  5 
snd_pcm                80516  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd                    56708  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25748  0 
agpgart                35284  2 nvidia,intel_agp


~$ lspci -vv 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1339
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

and I have unmuted/maxed out every channel in alsamixer but still no sound....

---

### Post by melissawm on 2008-06-12
Exactly the same problem here... In Hardy. Does anyone have a solution to this? I have already recompiled ALSA and everything, with no luck. One thing that bugs me is that 

```
dmesg | grep snd_
```

is empty; dmesg does not show snd_hda_intel or anything similar...

---

