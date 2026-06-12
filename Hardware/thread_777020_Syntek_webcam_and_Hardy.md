---
title: "Syntek webcam and Hardy"
date: 2008-05-01
forum: Hardware
---

### Post by bogdan_5844 on 2008-05-01
Back in 7.10,my syntek webcam worked only by much hassle with the sytnek drivers.
I am pleased to see that Hardy now detects my webcam correctly.Camorama gets the image from the webcam,so do other programs.Only problem is this: the image is upside down.

In Gutsy,when this occured I'd just

```
sudo rmmod stk11xx
sudo insmod stk11xx vflip=1
```

But it doesn't work now,because it complains that no stk11xx module was found.What should I do to get normal image back? :confused:

P.S.:Can't wait to use KDENLive to make videos recorded with my webcam :lolflag:

---

### Post by Nicolasto on 2008-05-01
> **bogdan_5844 said:**
> Back in 7.10,my syntek webcam worked only by much hassle with the sytnek drivers.
I am pleased to see that Hardy now detects my webcam correctly.Camorama gets the image from the webcam,so do other programs.Only problem is this: the image is upside down.

In Gutsy,when this occured I'd just

```
sudo rmmod stk11xx
sudo insmod stk11xx vflip=1
```

But it doesn't work now,because it complains that no stk11xx module was found.What should I do to get normal image back? :confused:

P.S.:Can't wait to use KDENLive to make videos recorded with my webcam :lolflag:
Try Cheese, with that should work and you can make videos!

---

### Post by bogdan_5844 on 2008-05-01
Cheese works nice,thanks ;)

Altough my webcam still is upside down in programs like Kopete,it`s no problem.I`ll use messenger in XP when I need webcam.

Thanks again,Nicolasto!

Ubuntu rocks,as usual!:popcorn:

---

