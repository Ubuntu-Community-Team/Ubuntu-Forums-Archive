---
title: "No sound HP Pavilion dv7"
date: 2009-11-06
forum: Hardware
---

### Post by Andrew.Z on 2009-11-06
I just installed Ubuntu 9.10 clean on an HP Pavilion Entertainment PC (notebook) dv7-3063cl, but there is no sound.  (I checked mute, volume, and various apps.)  The sound device is ATI Technologies (according to lspci).

EDIT: more details
```
$ lspci |grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc Device 970f
```

```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD75B3X5
Codec: LSI ID 1040

```

Here's 10 pages of [audio debugging output from an ALSA script](http://www.alsa-project.org/db/?f=416d907166e0ebe39b3c28101a5dc694aaa8a4a4)

---

