---
title: "problems tvout"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by tpariel on 2007-01-05
hi all,

I have Kubuntu (Dapper) inslled in my laptop with a Ati Radeon X600. I alredy inslled the latest driver and it works perfectly, 3D acceleration and everything works propeely. But when I tryied to watch movies throug the TV (using the s-video) it was imposible. The X is exported with out any problem and but I cannot see the movie it self. I can see the movie in the laptop but but on TV I just see the black window of the Mplayer or Kaffeine or whatever video player I have used.
Could any one help with this?
Thanks in advanced .
Ariel

---

### Post by steefjeqv on 2007-01-18
Hi,

You have to enable the overlay function for your tvout.

Open terminal and type "aticonfig". You 'll get a bunch of commands to configure your ATI card.

One of them is : aticonfig --overlay-on={0|1}
0 = your monitor, 1 = your TV.

The following command should do the trick :
sudo aticonfig --overlay-on=1

I hope the way your ATI card handles TV display turns out well, because I've had my share of troubles with my ATI 9000. In the end I changed to Nvidia.

Greetings,
Steven

---

### Post by neztiti on 2007-04-02
hi
how i can config my dxr3 with kaffeine to see on the tv

---

