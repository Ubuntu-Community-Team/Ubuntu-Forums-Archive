---
title: "Sound is not working! and no error found."
date: 2009-02-08
forum: Hardware
---

### Post by agape0131 on 2009-02-08
I have toshiba satellite M30.
The sound was working just fine till yesterday, and when I turned the computer on today, the sound is gone! I have no idea why it just stopped working.

When I type **aplay -l**, I get ```
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

One of the results of **lspci** gives me ```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

```

**modinfo soundcore** gives me this result: ```
filename:       /lib/modules/2.6.27-11-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 

``` which tells me that I don’t need to recompile your kernel?


I also did "Add to the end of /etc/modprobe.d/alsa-base:" ```
options snd-hda-intel model=3stack
``` but it still did not work.

My alsamixer is NOT muted, and The volume control is not muted, either. The device that the volume control chose is: Intel 82801DB-ICH4 (Alsa Mixer). Only the Master volume is all the way up.

However, the alarm sound only works when I am on terminal. When I mistype something or press TAB, it gives me the alarm sound that I did something wrong. Other than that, my computer produces no sound whatsoever.

I am indeed ubuntu newb, and please Help, please!

---

