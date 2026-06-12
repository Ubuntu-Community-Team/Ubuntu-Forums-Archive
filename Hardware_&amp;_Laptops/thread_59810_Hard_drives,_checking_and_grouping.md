---
title: "Hard drives, checking and grouping"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by qwert231 on 2005-08-25
Two questions here. I wanted to know where I could check the hard drives in Ubuntu, and see how much are used. I have a system w/ two drives, but I don't know if both are being used and if so, how much, and what is on each?

Second, can I have 2 or more hard drives joined together as one big root (/) partition? Or perhaps, 1 as root, and 2 or more as /www/?

---

### Post by s_p_a_r_k_y on 2005-08-25
typing in df into a console will show you how much of each drive is used. Usually the first hard drive is called hda, and any partitions on it are hda1...

If they are on the same cable then the other will be hdb

IF you want to join 2 drives together to make one big drive with nice performance, you want to do a raid0 setup. Googling around for it should give you lots of hits. How experienced are you with Linux as setting up a raid array is not childs play.

---

### Post by qwert231 on 2005-08-26
[QUOTE=s_p_a_r_k_y]typing in df into a console will show you how much of each drive is used. Usually the first hard drive is called hda, and any partitions on it are hda1...

If they are on the same cable then the other will be hdb

IF you want to join 2 drives together to make one big drive with nice performance, you want to do a raid0 setup. Googling around for it should give you lots of hits. How experienced are you with Linux as setting up a raid array is not childs play.[/QUOTE]
 I'm still a little new with Linux. But I'm very experienced with computers. Been fixing, building, and programming in the Dos/Windows world for almost 10 years.

---

### Post by qwert231 on 2005-11-14
Can I do a Raid0 with data existing on the drive? Or do/should they get wiped?

---

### Post by qwert231 on 2005-11-14
You can watch what I'm doing here:
[http://mkenyon2.blogspot.com/2005/11/current-activity.html](http://mkenyon2.blogspot.com/2005/11/current-activity.html)

---

