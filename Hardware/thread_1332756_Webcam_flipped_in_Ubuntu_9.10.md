---
title: "Webcam flipped in Ubuntu 9.10"
date: 2009-11-20
forum: Hardware
---

### Post by ashrafuzzaman2@ on 2009-11-20
Hi,
I am using Ubuntu 9.10 in ASUS x5dij series.
My built in webcam shows flipped image in skype and every where except [Cheese webcam]("http://projects.gnome.org/cheese/").

I have searched a lot in the forum but did not find any solution that works for me. Can anyone please help me?

---

### Post by JUMmi on 2009-11-21
Hi,

I had the same problem on my Asus V1J.
Try this:

echo 0 > /sys/class/video4linux/video0/vflip

or

echo 1 >/sys/class/video4linux/video0/vflip

If it's works, You can add that line to /etc/rc.local file and it's executed automatically when system starts.

Jarmo Uusi-Maahi
Jyväskylä, Finland

---

### Post by ashrafuzzaman2@ on 2009-11-21
Thanks for the suggestion
I tried that but I got

> /sys/class/video4linux/video0/vflip: No such file or directory

---

### Post by ashrafuzzaman2@ on 2009-11-21
Thanks for the suggestion
I tried that but I got

> /sys/class/video4linux/video0/vflip: No such file or directory

---

