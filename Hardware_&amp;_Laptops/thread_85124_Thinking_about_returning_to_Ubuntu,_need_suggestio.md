---
title: "Thinking about returning to Ubuntu, need suggestions"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by nickj6282 on 2005-11-01
I had Hoary installed on my Dell Inspiron 600m a few weeks ago. My hardware all worked great with it and I was very impressed. There were a few things that really annoyed me and ended up driving me back to Windows:

1. Slow-as-molasses CD ripping. Like 0.2-0.3x using both Sound Juicer and Grip trying many different options and configurations. Couldn't be helped.

2. No automatic connection to my bluetooth mouse. Every time I'd reboot I have to push the button on the mouse and issue the "hidd --connect [mac address of mouse]" command. Not a huge deal but still an annoyance.

3. Wireless network roaming. There didn't seem to be an obvious way to store profiles for multiple wireless networks, so when I'd go from work to home to mom's house to library etc. I'd have to change the wireless profile and wait every time. This also had the effect of adding a good 60 seconds to boot up if I was booting outside the range of the last used wireless network since it would hang while waiting for the network to respond (which it obviously never would).

Barring all that, I really do love Ubuntu and I'd like to switch back if possible. Does anyone know if these issues are fixed in 5.10? I downloaded the install/live DVD and burned it. I can boot it up dandily and use it fine, but due to the nature of a live CD distribution, I can't assess whether or not these problems still exist in Breezy.

Thanks a bunch for your help!
-Nick

---

### Post by GoodPanos on 2005-11-01
I'll tell you one thing you can do with the LiveCD, is check out the wireless.  That's how I checked mine.  It detected it right of the box.

As far as profiles though, I haven't come accross any funcionality like that.  Maybe a fellow member here can shed some light.  :D

---

### Post by nickj6282 on 2005-11-02
Oh I know the wireless will work without a hitch. It did before and it does with the live CD. I want to know if I'll have to wait an extra minute to boot if say I set the wireless up for my home network and then boot up at work or something like that.

Thanks
-Nick

---

### Post by `GooZ´ on 2005-11-02
wifi-radar (gnome) or Kwifi (KDE) support profiles. The wait-on-boot issue still remains, I'm afraid. But I've heard it's possible to switch it off on boot (search the forums). Luckily this problem will be fixed in Dapper Drake (next release).

---

### Post by BlueNoteMKVI on 2005-11-03
I've been dealing with the wireless profile issue for most of the day on two laptops here.  I think the solution for me is the package "whereami" - available in apt.  I found that this morning and I think I'm nearly done configuring it - it's been a long day.  I get very annoyed with tinkering sometimes, but I'm fairly certain that this system will run like a charm once I get everything set up.

---

