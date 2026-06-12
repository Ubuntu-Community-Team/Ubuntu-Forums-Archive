---
title: "no sound from x-fi titanium sound card"
date: 2008-11-01
forum: General Help
---

### Post by badperson on 2008-11-01
I went through this whole thing where I re-installed the linux kernel and used oss instead of alsa...

here's my results from osstest:

```
jason@jason-kubuntu:~$ osstest
Sound subsystem and version: OSS 4.1 (b rc1/200809232338) (0x00040090)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/oss_sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi output
- Performing audio playback test...
  <left> Device returned error: Input/output error
/dev/oss/oss_sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi input
- Skipping input only device

*** Some errors were detected during the tests ***
jason@jason-kubuntu:~$        
```

anyone have any idea how to fix this? 
thanks, 
bp

---

### Post by badperson on 2008-11-02
I was hoping that the upgrade to intrepid would magically resolve this issue...no luck
bp

---

