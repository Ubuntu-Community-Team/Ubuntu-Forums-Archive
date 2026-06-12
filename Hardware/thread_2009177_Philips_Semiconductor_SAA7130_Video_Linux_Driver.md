---
title: "Philips Semiconductor SAA7130 Video Linux Driver"
date: 2012-06-24
forum: Hardware
---

### Post by Hashnoit on 2012-06-24
Friends,
         I've recently switched from windows to Ubuntu (11.10). I loved it. But, I had my tv card fixed into the Mother Board.

I figured out that it's By 'lspci -nn'


[B]01:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
[/B]

I tried _tvtime_. But, it's all blue screen says;

[B]Frames too short from uvcvideo
   Cannot open capture device /dev/vidoe0.[/B]

Can somebody help me please ? I looked through so many threads
but as a total newbie I can't figure anything.

Please Help me.

---

### Post by typhoon_tip on 2012-06-24
Sorry but... why not try 12.04 which has a much newer Kernel ? 11.10 is pretty old now. There is a specific reason why you use 11.10 ?

---

### Post by Hashnoit on 2012-06-24
Thanks for the reply!
                      No, there's no specific reason. The installation disk I had was 11.10. (Which is given by a friend)

Will any ubuntu upgrading make solutions to the problem ?

---

### Post by typhoon_tip on 2012-06-24
> **Hashnoit said:**
> Thanks for the reply!
                      No, there's no specific reason. The installation disk I had was 11.10. (Which is given by a friend)

Will any ubuntu upgrading make solutions to the problem ?

Strongly suggest you to try 12.04 first. You can download at [www.ubuntu.com](www.ubuntu.com) via torrent file, it won't take long. Follow the instructions how to make a startup disk once downloaded the .ISO file (very easy with Ubuntu, just use the "Startup Disk Creator" program or write image .ISO to a CD, best of all is use a USB stick !).

---

### Post by Hashnoit on 2012-06-24
> **typhoon_tip said:**
> Strongly suggest you to try 12.04 first. You can download at [www.ubuntu.com](www.ubuntu.com) via torrent file, it won't take long. Follow the instructions how to make a startup disk once downloaded the .ISO file (very easy with Ubuntu, just use the "Startup Disk Creator" program or write image .ISO to a CD, best of all is use a USB stick !).

Thanks! Anyway, isn't there any solution for this other than upgrading Ubuntu Version ?

---

### Post by typhoon_tip on 2012-06-24
> **Hashnoit said:**
> Thanks! Anyway, isn't there any solution for this other than upgrading Ubuntu Version ?

Since is quite a complex issue, and may as well be dependent on drivers and firmware stuff, I suggest you try Ubuntu 12.04, even LiveCD to see if you get any lucky. If not, then we can look at plan B.

---

### Post by jmore9 on 2012-06-24
If you can figure out who made it it will go alot easier.  Also you can go to linuxtv.org and look around .

---

### Post by zouzou0 on 2012-07-07
i have this same card intex saa7130 and been trying for weeks on ubuntu 12.04 with no luck even if u upgrade it won't work it need alot of searching and working if I come up with a solution I will inform.

---

