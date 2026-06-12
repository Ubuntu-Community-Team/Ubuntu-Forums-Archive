---
title: "Sound Problem on Hp Pavillion dv5000"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by bod2na on 2008-03-12
Hi,
I'm a newbie ubuntu user. It's been a mounth since I've install ubuntu 7.10.
I have a problem which I'm not able to solve on my own.
I can't decrease or increase the volume from my desktop sound icon.
even I mute it It always makes sounds.
But while I'm listening to music or wathcing movies I'm able to decrease or increase the sound.
Anyone can help me?
Thanks

---

### Post by bod2na on 2008-03-12
nobody helps?

---

### Post by baluchi on 2008-04-08
This is a known bug, the volume controls won't control the actual sound:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93600](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93600)

Unfortunately, this bug continues to exist in 8.04beta.

What you can do though is control the volume through the volume applet then control the PCM value.

The work around on [https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d](https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d) might work, however I haven't tested it yet.

---

### Post by Redzin on 2008-06-10
I had the exact same problem as the OP described. I'm using a HP Pavilion dv5000 and the sound controls didn't work in 7.10/8.04.

Tried the fix on the mac-support site and it works great. :)

---

