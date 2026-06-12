---
title: "No /dev/sequencer? [OSS 4.1]"
date: 2009-01-20
forum: Hardware
---

### Post by talon314 on 2009-01-20
I have an Intel hda audio controller (lspci|grep Audio gives)

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

that I'm using with OSS 4.1 (pulse/alsa both fail to work for me). A few of my applications complain about a missing /dev/sequencer (including Frets on Fire and XMBC) and do not play audio. Does anyone else have this problem? Is there any way to create this device?

---

### Post by talon314 on 2009-01-23
Bump

---

### Post by talon314 on 2009-01-25
Well, Frets on Fire works now (albeit still with this error), although XBMC still does the play-videos-as-fast-as-possible-without-audio thing it does when audio isn't working. Perhaps /dev/sequencer isn't a problem... does anyone know how to get XBMC to play nicely with OSS?

---

