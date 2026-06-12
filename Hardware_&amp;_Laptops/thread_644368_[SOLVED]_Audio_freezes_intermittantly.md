---
title: "[SOLVED] Audio freezes intermittantly"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by lathanial on 2007-12-18
The audio on my wife's HP-510 works intermittently. When listening to music it plays for a while then stops for a few seconds to a few minutes then starts back. Does this on both Rhythm Box and Amrok. In general the system is unresponsive until it "unfreezes" itself. The date and clock continue to run and I can move pointer around but if I select another app  - a card game maybe - it won't start until music starts back up.

The sound device is Intel's ICH6 family AC'97 audio controller (82801) if that helps. If you need more information let me know.

I find that when my wife isn't happy neither am I. Any help appreciated.

---

### Post by lathanial on 2007-12-22
Come on folks. I know the Holiday season is upon us and things may be hectic but all I'm asking is a nudge in the right direction. I haven't been able to find any post related to my problem but I found some post about odd problems on a dual boot machine. I didn't think it was important but I am dual booting this HP-510 laptop with winXP Pro and Ubuntu 7.04. Everything works fine under winXP. The only apparent problem with Ubuntu is that when playing music it intermittently stops and starts. When it stops I can't start additional apps but I can usually continue using any currently open apps.

If anyone has seen post that may be related please point me in the right direction.

Happy Holidays to all

---

### Post by lathanial on 2007-12-23
Just in case anyone is interested, I think the problem is solved - although I don't know why. After looking at some post regarding a problem with Sound Blaster driver, I tried modifying /etc/modprobe.d/options. This killed all of my sound. I removed the entry in that killed the audio and now audio works fine. Anyway, although my problem is solved if anyone has an idea why this would make a difference I would like to hear from you.

Thanks,
lathanial

---

