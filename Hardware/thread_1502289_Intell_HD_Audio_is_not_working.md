---
title: "Intell HD Audio is not working"
date: 2010-06-05
forum: Hardware
---

### Post by khalid.A on 2010-06-05
I have bought a new Dell Studio laptop and installed ubuntu (dual booting with Win7). The problem I'm having is that the audio card, which is Intel Integrated High Definition Audio 2.2, is not working at all. I have tried to install linux-backports-modules-alsa-2.6.32-22-generic but this hasn't fixed it yet.
Below is the output of cat /proc/asound/cards 
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0700000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfeec000 irq 17

```
And this is the output of lspci | grep -i audio
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc RV710/730

```

Thanks in advance, and any solution will be welcomed.

---

### Post by khalid.A on 2010-06-05
I just solved it by doing the following:
```
cd ~/alsa-driver-1.0.16
./configure --with-cards=hda-intel
```

---

