---
title: "HP dv5-1102tu Not able to hear sound in speaker."
date: 2008-10-02
forum: Hardware
---

### Post by zoobave on 2008-10-02
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

I installed ubuntu 7.10 on my new HP dv5-1102tu laptop. I can able to hear the sounds in my head phone. but, my laptop speaker is not working.

```
zoobave@zoobave-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
zoobave@zoobave-laptop:~$ cat /proc/asound/card*/codec#0 | grep -i codec
Codec: Generic 111d ID 76b2

```

please help me regarding this issue

---

### Post by zoobave on 2008-10-03
its an altec lansing speakers

---

### Post by jonbonjovi on 2009-01-26
I have sound issues on my HP dv5 too. I installed 8.10 and I can't use the mic and when I reboot the speakers/headphones make a very noisy cracking noise.

have you found a workaround? My sound card is the same as yours.

---

