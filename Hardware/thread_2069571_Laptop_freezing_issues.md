---
title: "Laptop freezing issues"
date: 2012-10-11
forum: Hardware
---

### Post by COKEDUDE on 2012-10-11
I am having Laptop freezing issues. Whenever I try to use Firfox and vlc, chrome and vlc, firefox and chrome, or anything similar to that my computer freezes. I always have to kill one of the processes before I can use my laptop again. I am guessing this is a hardware issue because when I move the HD to my other laptop it works just fine without freezing. I can also move my HD from my good laptop and put it in my old laptop and the same thing happens with the freezing. Can I please get some ideas on what the problem is?

---

### Post by coldraven on 2012-10-11
Try booting from a live CD and run the Memory Check utility. I think it takes a while so maybe do it overnight.
You could also check for overheating
```
sudo apt-get install psensor

```
If your laptop is running hot then the fan probably needs cleaning. This five year old machine was half choked with fluff, now it is cool and quiet.

---

### Post by COKEDUDE on 2012-10-11
> **coldraven said:**
> Try booting from a live CD and run the Memory Check utility. I think it takes a while so maybe do it overnight.
You could also check for overheating
```
sudo apt-get install psensor

```
If your laptop is running hot then the fan probably needs cleaning. This five year old machine was half choked with fluff, now it is cool and quiet.

Why do you think it is ram instead of cpu issue? I was thinking it was a cpu issue. Ram is much easier to replace so I hope your right.

---

### Post by ahallubuntu on 2012-10-11
No one here knows what is wrong with your laptop.  We can only give you tips on systematically testing things and ruling out likely causes.  Testing your RAM is easy - Memtest is installed with Ubuntu.  If the laptop is more than a year or two old, I would clean out the CPU heat sink/fan area too, and make sure the fan is working.

If the CPU isn't overheating due to dirt/dust and the RAM tests out OK, then you may have some difficult-to-fix motherboard issue.

---

### Post by COKEDUDE on 2012-10-17
> **coldraven said:**
> Try booting from a live CD and run the Memory Check utility. I think it takes a while so maybe do it overnight.
You could also check for overheating
```
sudo apt-get install psensor

```
If your laptop is running hot then the fan probably needs cleaning. This five year old machine was half choked with fluff, now it is cool and quiet.

I used memtest86+ and it could not find any errors. Is psensor better than memtest86+? 

What would you recommend testing next?

---

### Post by ahallubuntu on 2012-10-17
Check the CPU/heat sink fan for dirt and dust as I described above, and make sure the fan is actually working.

---

