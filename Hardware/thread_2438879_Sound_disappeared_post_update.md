---
title: "Sound disappeared post update"
date: 2020-03-19
forum: Hardware
---

### Post by sven-lmb on 2020-03-19
Hei everyone,
I know this issue has been posted and solved on many threads around the net, but after many hours trying everything, nothing works. So here is my situation:
* The sound disappeared yesterday. That means no output from the inbuilt speakers nor the earphones. I have "dummy output" shown in the settings, and my audio card isn't there. I did a requested update the same morning, but I am not sure if this is linked. I don't remember what the update was about. I use ubuntu 19.10.; Acer aspire V nitro laptop.
* I have seen many "solutions" everywhere, but nothing worked. The purging of Alsa and pulse does not help. Btw, "alsamixer" in the terminal tells me that there is no such file or directory.
* I tried playing around in the in the alsa-base.conf file, with no more luck.
* I cannot find anything linked to the sound in my BIOS. So I cannot say if it is enabled or not.
* Running ```
~$ lspci -v | grep -A7 -i "audio"
```    gives me this:
```
00:1f.3 Multimedia audio controller: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
    Subsystem: Acer Incorporated [ALI] 100 Series/C230 Series Chipset Family HD Audio Controller
    Flags: fast devsel, IRQ 16
    Memory at 84320000 (64-bit, non-prefetchable) [size=16K]
    Memory at 84310000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: snd_hda_intel
```

I am a bit lost right now. Any idea? Thanks for the help!

---

