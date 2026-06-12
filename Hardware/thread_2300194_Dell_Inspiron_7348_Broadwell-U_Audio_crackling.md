---
title: "Dell Inspiron 7348 Broadwell-U Audio crackling"
date: 2015-10-24
forum: Hardware
---

### Post by simone-aonzo on 2015-10-24
After a fresh installation of Ubuntu 15.10 the audio is always crackling...

```
simo@hell:~/android-studio/bin$ cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xc1118000 irq 48
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc111c000 irq 47
simo@hell:~/android-studio/bin$ sudo lspci -v | grep -i audio
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
```


After googoling I haven't solved the problem and the last entry of my /etc/modprobe.d/alsa-base.conf is:
```

options snd-hda-intel model=dell power_save=0 power_save_controller=N

```

Thanks for help.

---

