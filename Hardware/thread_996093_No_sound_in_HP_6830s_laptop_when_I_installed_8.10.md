---
title: "No sound in HP 6830s laptop when I installed 8.10"
date: 2008-11-28
forum: Hardware
---

### Post by VOVEEE on 2008-11-28
Hi everybody!

I have this annoying problem - I don't have a sound on my HP 6830s laptop. Everything was OK when I was using 8.04 - after fresh install I updated alsa drivers to the newest version and the sound was working. But before a couple days I formated my HDD and installed 8.10. After that there is no sound on my machine. I tried this - [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and some other stuff but there is no effect. The most interesting thing is that in my dmesg there is no snd_ tag. What can I do to make my sound work?

---

### Post by psimmering on 2008-12-04
Hello,
I have the same problem and so does a colleague of mine, who noticed that sound ***does*** work over the headphones connector. So you **can** hear something...
Peter

---

### Post by harmenw on 2008-12-14
I had the same problem on HP 6830s and found the solution on:
[http://www.linlap.com/wiki/HP-Compaq+6730S](http://www.linlap.com/wiki/HP-Compaq+6730S)

I just added to /etc/modprobe.d/alsa-base the following line:
options snd-hda-intel model=laptop enable=1 index=0

---

### Post by amin5236 on 2009-02-12
I had the same problem, ubuntu 8.10 on HP 6730s. I updated ubuntu online, then it worked properly :)

---

### Post by squenson on 2009-03-07
> **harmenw said:**
> I just added to /etc/modprobe.d/alsa-base the following line:
options snd-hda-intel model=laptop enable=1 index=0
Thank you harmenw, your solution worked very well for me!

---

