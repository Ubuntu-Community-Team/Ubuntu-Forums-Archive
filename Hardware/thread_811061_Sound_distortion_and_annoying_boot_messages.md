---
title: "Sound distortion and annoying boot messages"
date: 2008-05-28
forum: Hardware
---

### Post by timothius on 2008-05-28
Hi,

When I boot I get the following errors (Errors found by using dmesg | grep alsa):
```
May 29 00:19:56 hplappy kernel: [   47.799470] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2061: AC'97 1 does not respond - RESET
May 29 00:19:56 hplappy kernel: [   47.833344] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2070: AC'97 1 access is not valid [0xffffffff], removing mixer.
May 29 00:19:56 hplappy kernel: [   47.855456] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ali5451/ali5451.c:1927: ali mixer 1 creating error.
```

Does anyone know how to remove these?  This only happened after I installed the packages suggested in this howto:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I have tried to remove the packages that installed, but the errors still remain.  

My second problem is that my sound crackles and the sound speeds up and slows down at random.  I've tried pretty much everything to sort this out, but to no avail.  Has anyone had similar issues?

My sound card model is:

```

A5451

```

Thanks for the help :)

---

