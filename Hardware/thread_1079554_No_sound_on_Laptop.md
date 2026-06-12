---
title: "No sound on Laptop"
date: 2009-02-24
forum: Hardware
---

### Post by jamal247e on 2009-02-24
Hello everyone,
I've installed Ubuntu 8.10 on my laptop recently,
But there is no sound output! and I can not hear anything!
My Laptop details:
Gateway, Pentium4 and 1.8 dual processor

Here are some details which might be helpful:

```

asoundconf list:
Names of available sound cards:
I82801DBICH4

```

```

asoundconf:
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio
asoundconf set-oss PARAMETER
asoundconf unset-oss

```

```

cat /proc/asound/cards:
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with unknown codec at irq 17

```

```

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Please help me to fix it and be able to listen to the Music :guitar:

---

### Post by kehaar on 2009-03-02
I have this exact configuration and this exact problem. I have tried several solutions proposed online that did not help. Any advice would be appreciated. Switching to openSUSE if I can't get my sound to work.

---

