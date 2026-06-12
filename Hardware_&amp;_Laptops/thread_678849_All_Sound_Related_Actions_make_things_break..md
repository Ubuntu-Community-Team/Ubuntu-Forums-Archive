---
title: "All Sound Related Actions make things break."
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by shoeshrimp on 2008-01-26
Is my technical way of saying - whenever I try to do anything sound related, play a music file, audio cd, test sound etc. The program I am running crashes. My laptop is running a realtek AC97 soundcard. The only sound related thing that does work is the log-in sound. I really don't know what's going on - and am not sure if my computer is even detecting my sound card. Any information as to where to go from here would be fantastic! Thanks.

Tom

---

### Post by shoeshrimp on 2008-01-26
i also get:

tom@tom-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
tom@tom-laptop:~$ sudo modprobe snd-
[sudo] password for tom:
FATAL: Module snd_ not found.


any ideas?

---

### Post by shoeshrimp on 2008-01-27
*bump* - sorry guys, am struggling with this!

---

