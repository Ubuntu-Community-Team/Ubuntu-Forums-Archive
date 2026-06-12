---
title: "onboard sound not recognized"
date: 2009-06-14
forum: Hardware
---

### Post by sp0tz on 2009-06-14
I recently installed ubunto on a computer with onboard sound. The motherboard is a GA-K8NS nForce3. 

The onboard sound does not seem to be recognized. I've got some speakers plugged in, and no sound comes from them. Running alsamixer fails like this:

```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```
```


cat /proc/asound/cards
```
returns this:
```
--- no soundcards ---
```


lspci returns this:

```
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

... No sound, sound card not recognized. I've had sound come from this machine before, even with ubuntu. I think I had to jump through some hoops to get it working, though. If I remember right it had something to do with the motherboard model number. No luck searching with google, though. Can I get some help?

---

### Post by sp0tz on 2009-06-14
sp0tz, you sexy genius, if lspci returns this:

```
 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

```
then you should paste this into your /etc/modprobe.d/alsa-base file:
```
# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-intel8x0
options snd-intel8x0 index=0
options snd-intel8x0 buggy_semaphore=1
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

# OSS/Free portion - card #1
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

# OSS/Free portion - card #2 (cmipci)
alias sound-slot-1 snd-card-1
alias sound-service-1-0 snd-mixer-oss
alias sound-service-1-3 snd-pcm-oss
alias sound-service-1-12 snd-pcm-oss
```

as per this forum post:
[http://ubuntuforums.org/showthread.php?t=317061](http://ubuntuforums.org/showthread.php?t=317061)


Also, your laundry is done.

---

### Post by majamba on 2009-06-14
ubuntu soundguide hopefully this helps
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

