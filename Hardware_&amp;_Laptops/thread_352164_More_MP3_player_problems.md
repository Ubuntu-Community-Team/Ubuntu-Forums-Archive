---
title: "More MP3 player problems"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by mjskia1 on 2007-02-02
I'm trying to get a SanDisk Sansa m240 mp3 player working under 64-bit Ubuntu Edgy.  I've read the previous posts, and I thought I did everything right.  I switched it to MSC and plugged it in, and Ubuntu recognized and mounted it, and even started Rhythmbox.  Problem is, none of them can actually see any music on the thing.  I uploaded all of the music from Windows, so the vast majority of it is WMA, but I know that at least a handful of the files on there are MP3.

Here's what ls -aR reports on the player (mounted at /media/Sansa m240):
```
~$ ls -aR /media/Sansa\ m240/
/media/Sansa m240/:
.  ..  AUDACT.TCC  AUDIBLE  CONFIG  RECORD  SYS_CONF.DNC

/media/Sansa m240/AUDIBLE:
.  ..

/media/Sansa m240/CONFIG:
.  ..  CONFIG.TCC

/media/Sansa m240/RECORD:
.  ..

```

Nautilus reports the same thing -- there's no MUSIC directory to be found.  Nautilus does correctly report that only 471 MB of the player's 1 GB capacity is free, but provides nothing else. 

Further investigation through the device manager revealed that the player is mounted as a SCSI device over USB and is apparently at /dev/sda1.  (I confirmed this by recognizing a couple of mp3 song titles in the stream of gibberish that whizzed by when I typed cat < /dev/sda1.) 

In short, I'm stumped.  Any ideas?

---

### Post by atihimself on 2007-05-26
I have same problems, and my pc thinks its a camera

---

### Post by mjbauer95 on 2008-05-29
Sorry to revive this old thread but I am also having the same problem.

---

