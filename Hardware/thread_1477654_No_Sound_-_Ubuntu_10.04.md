---
title: "No Sound - Ubuntu 10.04"
date: 2010-05-09
forum: Hardware
---

### Post by TheStagesmith on 2010-05-09
I am running Ubuntu 10.04 32-bit on an ASUS G51vx (the Best Buy one). I have previously run Ubuntu 9.10 and Fedora 12 on it with very few issues. However, upon recently installing Lucid Lynx on it, I've found that the system will not play sound of any kind. I tried installing updated ALSA drivers using the advice of a few threads on these forums, but I haven't gotten it to work by myself. Now I'm trying to find someone who can help me with my problem. 

Attached below are a few snippets of information I gathered and (I hope) are relevant. I'd appreciate any advice I can get. Thank you!

Output of uname -a:
```

Linux Rocky-L 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```

Output of aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Output of cat /proc/asound/version:
```

Advanced Linux Sound Architecture Driver Version 1.0.21.

```

Output of head -n 1 /proc/asound/card*/codec#* :
```

Codec: Realtek ALC663

```

---

### Post by TheStagesmith on 2010-05-11
Bumped for I really need help with this?

---

### Post by lidex on 2010-05-13
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by andon21 on 2010-08-01
not trying to raise the dead, just wondering if this solution worked. Having the same problem and am supremely frustrated

---

### Post by lidex on 2010-08-01
> **andon21 said:**
> not trying to raise the dead, just wondering if this solution worked. Having the same problem and am supremely frustrated

We may never know if it worked for the OP, but even if it did, you would need to have the same hardware for it to help you. If you do, try it and see.

---

