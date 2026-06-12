---
title: "Yet another sound problem..."
date: 2010-06-23
forum: Hardware
---

### Post by DerRosaElefant on 2010-06-23
Hello all,

I am using Ubuntu 10.04 and have a problem with my sound... When I plug in headphones or external speakers, they do work, but the internal speakers also continue playing... I have searched extensively but have been unable to find anything that works for my specific laptop. I may have missed something, and if I have, I apologize. Any help would be appreciated, would much rather use this OS than Windows, but this situation is pretty much a dealbreaker...

Here's some info that might help (It's an acer Aspire 7740 )

```

uname -a
Linux UbuntuLaptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 670

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

```

---

### Post by DerRosaElefant on 2010-06-24
Not trying to be annoying... Just thought I would give this a bump and see if anyone might have any advice before I head back to Windows later :-k

---

### Post by Yellow Pasque on 2010-06-24
The realtek alc670 just gained support in ALSA 1.0.23, so: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by DerRosaElefant on 2010-06-24
Great! Thank you so much for that link :) I will give it a try when I can, and see how it works!

---

### Post by DerRosaElefant on 2010-06-25
Took a while for the process to finish, but, it worked like a charm! Thanks! :D

---

