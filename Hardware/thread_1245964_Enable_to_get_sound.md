---
title: "Enable to get sound"
date: 2009-08-21
forum: Hardware
---

### Post by ProgVal on 2009-08-21
Hello,

I'm a french user of Ubuntu, and I tried to get solution on the french support forum, but I can't get any.

My problem is the following: I can't have sound on Linux (but it works on Windows); I've tryed many distributions: Ubuntu, Kubuntu, and Sabayon (a Gentoo-like, with close-source drivers pre-installed).
I can get a few sound at the Kubuntu startup and shutdown, but the quality is very bad.

I've verifyed in the AlsaMixer, and nothing is mute.
There is also a surprising thing: the sound works when I run programms under Wine (FireFox, Opera, Teeworlds (a little game), ...)

My configuration is the felloing:
- HP Pavilion dv7 Notebook PC
- Intel Centrino2 inside
- HDA intel sound device
I've tryed under this kernels:
- 2.6.28 (generic)
- 2.6.30.3 (non-generic)

Thank you for advance,
ProgVal

---

### Post by ProgVal on 2009-08-24
If I had bad translated, notify me, I'll try again.

---

### Post by ProgVal on 2009-08-24
I forgot to they that at the startup and the shutdown, I get a few sound, with a very bad quality

---

### Post by ProgVal on 2009-08-28
Up

---

### Post by Syniurge on 2009-09-01
Hello again ProgVal :D,

ALSA made a new release two days ago, with some fixes for Pavilion notebooks, perhaps well yours: [http://www.alsa-project.org/main/index.php/Changes_v1.0.20_v1.0.21#HDA_Codec_driver](http://www.alsa-project.org/main/index.php/Changes_v1.0.20_v1.0.21#HDA_Codec_driver)

The release will only be merged in the 2.6.32 kernel, but you might want to test it by replacing your current Ubuntu kernel modules, using the tarball from the ALSA homepage:

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
tar jxf alsa-driver-1.0.21.tar.bz2
cd alsa-driver-1.0.21
./configure --with-oss=yes --with-pcm-oss-plugins=yes && make && sudo make install
```

Reboot and test. If this solves your problem, keep in mind that the modules will need to be rebuilt and reinstalled after each Ubuntu kernel update.

Syn.

---

### Post by ProgVal on 2009-09-06
Sorry, it don't works...

---

