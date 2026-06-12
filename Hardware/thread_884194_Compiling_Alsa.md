---
title: "Compiling Alsa"
date: 2008-08-08
forum: Hardware
---

### Post by daz0001 on 2008-08-08
Should the Alsa build process copy its modules under the /lib/modules/`uname -r` directory?

It didn't seem to?

I only got my sound card to work by manually copying the files across?

---

### Post by phidia on 2008-08-08
If you're building from source, and you are, the alsa maintainer may have a different default build directory than what the ubuntu devs use.
Glad it works though-what did you need to get working-that wasn't working before?

---

### Post by daz0001 on 2008-08-08
ok, well I have a Thinpad T61, with sound device:
 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 

Installed Ubuntu 8.04.1 desktop, everything worked out of the box. 
Then for fun I decided to build a 2.2.26 kernel from kernel.org. 
This built and installed ok, but the sound no longer worked. 

I downloaded Alsa, followed the doc:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

but found that the snd_hda_intel could not be found. It seems that the kernel modules (*.ko) files that were under the /usr/src/alsa* directory did not get copied to the appropriate /lib/module directory?

Once I manually copied the files to what seemed like the correct directories, everything worked?

---

### Post by Nepherte on 2008-08-09
Try these commands:
```
cp -v /lib/modules/2.6.26-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.26-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.26-*/kernel/sound/
depmod -a
```

That worked for me back after I compiled alsa on Gutsy.

---

