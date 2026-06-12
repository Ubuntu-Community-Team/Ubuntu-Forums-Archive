---
title: "Laptop Model DV7-3065DX"
date: 2010-01-13
forum: Hardware
---

### Post by ChristopherO on 2010-01-13
I currently have no sound I checked, and nothing is muted, The hardware seemed to find it self and install it in the sound manager it shows the sound card, 

And my wireless light keeps blinking on and off, does not seem to interrupt  my services.

---

### Post by mk1w86 on 2010-01-13
I am not sure if it will fix the problem but have a look here:

[http://ubuntuforums.org/showthread.php?t=1339859](http://ubuntuforums.org/showthread.php?t=1339859)

---

### Post by ChristopherO on 2010-01-13
Re: HP DV7, No Sound with 8.04, or 9.10
1) Get hda-verb utility (Do a goole search for it) and install it.

2) Add the following to the /etc/rc.local startup script:
[B]
/usr/local/sbin/hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_MASK 3
/usr/local/sbin/hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_DIRECTION 1
/usr/local/sbin/hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_DATA 1

Make sure none of the volume settings are low or muted.

Reboot. You should now have sound.

from [http://www.kr.xemacs.org/pub/linux/k...misc/hda-verb/](http://www.kr.xemacs.org/pub/linux/k...misc/hda-verb/)




I can not find this Down load and i do not know how to add to startup script , I dl ubuntu cause im learning it in school and i want a head start, so im very new :S[/B]

---

### Post by ChristopherO on 2010-01-13
bump

---

### Post by ChristopherO on 2010-01-14
Still is not working I do not know how to add to start up like eh said, I did install that program still no sound though :S can any one else help

---

### Post by Keikowned on 2010-07-16
^o^

---

