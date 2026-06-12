---
title: "Adobe AIR - Install AdobeAIRInstaller.bin"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by paprikk on 2009-02-11
I need to install **Adobe AIR in Ubuntu 8.04** but the file is a .bin and I don't know how to run it... Can somebody give me a hand, please?:)

---

### Post by Partyboi2 on 2009-02-11
Open a terminal (Applications>Accessories>Terminal) and change directory to where the downloaded .bin file is. So if its on your Desktop 
```
cd ~/Desktop
```then
```
chmod +x AdobeAIRInstaller.bin
```folllowed by
```
./AdobeAIRInstaller.bin
```

---

### Post by paprikk on 2009-02-11
THX a lot!!!! Great, now I can install TweetDeck.:P

[I own you one]:smile:

---

### Post by ChrisMc73 on 2009-05-05
I tried these same exact steps and got this error next...

Error loading the runtime (/tmp/air.3ZPpYb/build/opt/Adobe AIR/Versions/1.0/Resources/libicudata.so.36: file too short)

I just want to install AIR, using 9.04...

---

### Post by muralbens on 2009-09-08
I followed the same steps and I could install Adobe AIR in Ubuntu 9.04.

Thanks a lot

Cheers,
Murali

---

### Post by LaneLester on 2009-09-20
AIR seems to install OK, but any app I try to install just dies during the install process. This was with Jaunty and now Karmic A6. Some months ago I did not have this problem; don't know what changed.

Lane

---

### Post by steveh1001 on 2009-10-07
Lane - does your machine have a 64 bit AMD processor?  Air won't work properly on those processors, even when running 32 bit Ubuntu.

---

### Post by LaneLester on 2009-10-07
> **steveh1001 said:**
> Lane - does your machine have a 64 bit AMD processor?  Air won't work properly on those processors, even when running 32 bit Ubuntu.
Yes, it does! That's exactly my situation. I'm glad the mystery is solved, even though it's not quite what I would have wanted.

Adobe must have changed something, because I was able to successfully run AIR apps on this machine for some time, and then suddenly, not!

Thank you for responding.

Lane

---

