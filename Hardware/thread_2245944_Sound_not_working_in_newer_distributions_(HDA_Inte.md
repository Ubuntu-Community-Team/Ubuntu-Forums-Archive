---
title: "Sound not working in newer distributions (HDA Intel - ALC269)"
date: 2014-09-27
forum: Hardware
---

### Post by simenrf on 2014-09-27
Running Xubuntu 12.04 has sound working fine. However, if I try newer versions of any Linux distro my soundcard is not working. For instance in Xubuntu 14.04, 14.10b2, Debian "jessie", Linux Mint 17 and OpenSuse 13.1 I have no sound. I assume this has to do something with the kernel version since older versions seems to work fine.
Googling the problem came up with similar problems and most seemed to be solved by editing ***/etc/modprobe.d/alsa-base.conf***. I tried this as well and played around with ***model=*** and tried several different models found in [*HD-Audio-Models.txt*]("http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD") but the result is always the same.
Sound settings on the desktop only shows "Dummy output".

_ Here is the ALSA information gathered by alsa-info.sh:_
From the not working xubuntu 14.04: [http://pastebin.com/zm936Y49](http://pastebin.com/zm936Y49)
From the working xubuntu 12.04: [http://pastebin.com/9ZHFPc5Z](http://pastebin.com/9ZHFPc5Z)

As you can see from the not working one ***aplay ***shows nothing, but on the working one ***aplay ***shows 
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

Any help would be appreciated.

---

### Post by Yellow Pasque on 2014-09-27
The first thing I would try is installing latest driver (and then rebooting) to make sure the issue has not already been fixed:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Other than that, you may want to google "hda-codec: out of range cmd"
```
[  101.096103] SKU: override=0x1
[  102.100207] hda-codec: out of range cmd 0:20:400:ffff7fff
```

Of course, you can always file a bug if those things don't work (make sure to remove any model customizations in alsa-base.conf first).
```
ubuntu-bug audio
```

---

### Post by simenrf on 2014-10-07
This problem has now been reported as a bug.
[https://bugs.launchpad.net/bugs/1375022](https://bugs.launchpad.net/bugs/1375022)

---

