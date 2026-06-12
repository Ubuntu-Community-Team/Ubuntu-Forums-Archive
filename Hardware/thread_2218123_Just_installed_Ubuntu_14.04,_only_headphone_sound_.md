---
title: "Just installed Ubuntu 14.04, only headphone sound (Realtek ALC283)"
date: 2014-04-19
forum: Hardware
---

### Post by csaorl on 2014-04-19
Hello everyone,

I just installed Ubuntu 14.04 on a Dell 7537. So far everything is working fine, except the sound: the built-in speakers won't work, but I do get sound if I plug my headphones. I already tryed checking the levels in alsamixer with no luck. 

I also tried the solution on this thread [http://ubuntuforums.org/showthread.php?t=2074897](http://ubuntuforums.org/showthread.php?t=2074897) but it didn' t work for me. 

Any ideas on what can I do to solve this? Any help would be much appreciated.

---

### Post by csaorl on 2014-04-19
Well audio works fine now. Adding the line ```
options snd-hda-intel model=auto
``` to ```
/etc/modprobe.d/alsa-base.conf
``` did the trick. Also, I left unchanged the modifications from the post I linked earlier.

---

