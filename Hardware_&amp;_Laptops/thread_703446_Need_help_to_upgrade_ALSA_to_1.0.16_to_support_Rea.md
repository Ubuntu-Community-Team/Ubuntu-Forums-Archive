---
title: "Need help to upgrade ALSA to 1.0.16 to support Realtek 268 with Intel HDA"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by tarun2000 on 2008-02-21
Hi, 

Im trying to upgrade alsa after reading that the newer versions support my soundcard.
I am able to do configure make and install for the lib and driver, but the utils package gives me errors on make.  I tried installing as myself and as root, both give the same error.  Any help would be appreciated.

```

Making all in include
make[1]: Entering directory `/home/tarun/alsa-utils-1.0.16/include'
make  all-am
make[2]: Entering directory `/home/tarun/alsa-utils-1.0.16/include'
make[2]: Leaving directory `/home/tarun/alsa-utils-1.0.16/include'
make[1]: Leaving directory `/home/tarun/alsa-utils-1.0.16/include'
Making all in alsactl
make[1]: Entering directory `/home/tarun/alsa-utils-1.0.16/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/tarun/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/tarun/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Entering directory `/home/tarun/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/tarun/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tarun/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1
```

---

### Post by Yellow Pasque on 2008-02-21
Maybe try this script?:
[http://ubuntuforums.org/showpost.php?p=4360698&postcount=6](http://ubuntuforums.org/showpost.php?p=4360698&postcount=6)

---

### Post by tarun2000 on 2008-02-21
alsa_2.sh gives me the following errors:
```

`/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/ac97_bus.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ac97-codec.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ad1816a.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ad1848-lib.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ad1848.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ad1889.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-adlib.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ak4114.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ak4117.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ak4531-codec.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-ak4xxx-adda.ko': No such file or directory
...

```
It continues with more missing files, but I can find the files manually.  ALSA 1.0.16 does seem to be in the kernel though, but still no sound.  The alsamixer shows that all channels are at full volume and recognizes the Realtek ALC268 chip.  What else could be wrong?  Is there a separate place to unmute the channels or does alsa_2.sh need to do some more essential configuring?

Nevermind, resetting some permissions fixed it, thank you very much for your help.

---

### Post by White_Panther on 2008-02-23
to run these scripts and get them to work, I cahnged the permissions and mede them executable first.  Then ran

```

sudo '/home/"your name"/Desktop/alsa_1.sh'
sudo '/home/"your name"/Desktop/alsa_2.sh'

```

just replaced your name with your computers name.

Edit: I have a Toshiba satellite A235-sXXXX

---

### Post by jedisitharg on 2008-03-12
Perfect!! Thanks for the scripts!
For some reason wget was giving "no route to host..", but I've  downloaded the required files via Firefox, and commented the wget lines in alsa_1.sh, and everything was ok

---

