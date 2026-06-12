---
title: "HP notebook sound problem"
date: 2010-06-02
forum: Hardware
---

### Post by renke86 on 2010-06-02
I have Lucid on my HP nc6220. The speaker works fine, when I plug in my earphone in the jack slot the speaker get muted, and when my plug out the earphone the speaker stays muted, but there is sound when I plug in the earphone again.

I have the latest alsa installed.

Any solutions?

---

### Post by lidex on 2010-06-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by renke86 on 2010-06-03
My laptop is HP Compaq nc6220m with Intel Pentium M 1,86 GHz processor and 1 GB RAM.

The outputs:

uname -a
```
Linux reni-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

cat/proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

head -n 1 /proc/asound/card*/codec#*
```
head: ”/proc/asound/card*/codec#*” cannot open for read: file or folder doesn't exist

```

Thanks for your help.

---

### Post by renke86 on 2010-06-03
I think I solved it.
I installed ALSA mixer and checked Headphone Jack Sense, and it seems to be working.

update: Sadly it work till the first restart, so I'm still looking for the solution:(

---

