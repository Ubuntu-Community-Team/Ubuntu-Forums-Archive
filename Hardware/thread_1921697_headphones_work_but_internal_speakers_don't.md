---
title: "headphones work but internal speakers don't"
date: 2012-02-07
forum: Hardware
---

### Post by andreasml on 2012-02-07
Hi,

I have installed Ubuntu 10.04. from
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

on my new hp 635 laptop. My problem is that my internal speakers are not working (but they arent blown, since they work on my other operating system), tough my headphones are. The speakers are from the manufacturer Altec Lanting.

From similar threads I have found, e.g.
[http://ubuntuforums.org/showthread.php?t=1837491&highlight=sound+headset](http://ubuntuforums.org/showthread.php?t=1837491&highlight=sound+headset)

I guess I have to change something in the file
/etc/modprobe.d/alsa-base.conf

I tried for example to attach
options snd-hda-intel enable_msi=1

at the end of the file and some other commands I have found, but every time after I rebooted it didnt work. I guess it is because I have a different sound card and have to use a command that is adapted to my hardware?


I hope you can help me, and please tell me if you need to know anything more (at best also tell me the terminal command I would have to use to obtain the necessary information; I am relatively new to linux, so please have mercy if I sound stupid)
Thanks, in advance.

---

### Post by andreasml on 2012-02-07
when I do sudo aplay -l i get

card 0: Generic [HD-Aufio Generic], device 3: ATI HDMI [ATI HDMI]
  sub device: 1/1
  sub device #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  sub device: 1/1
  sub device #0: subdevice #0

---

