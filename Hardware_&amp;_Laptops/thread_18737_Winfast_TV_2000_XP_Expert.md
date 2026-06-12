---
title: "Winfast TV 2000 XP Expert"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by Malroy on 2005-03-08
Hi,


I have big problem to run this card in ubuntu -  -  - on tvtime I have in dark-white colours, and no sound - what i have to do to run this card. Pls help me, is anyone runs this card... pls let me know.


Malroy

---

### Post by simsypoo on 2005-03-11
It's probably the bttv module setting the tuner to the wrong type.

I have the same problem. I have the Winfast TV 2000 XP Deluxe. I've had the issue resolved in the past by going into the /etc/modprobe.d directory and adding this line to a new file under the directory (I haven't tried this yet in Hoary, but I've had to do this before using a different distribution):

options bttv card=34 tuner=2

Let me know if it works.

Also found an archived thread here regarding the same issue:
[http://ubuntuforums.org/archive/index.php/t-360.html](http://ubuntuforums.org/archive/index.php/t-360.html)

---

### Post by dikki on 2005-03-12
I had the same problem, tried the modules.d file, but no success.

---

### Post by pt123 on 2005-07-08
I found a solution to the colour problem. When its black and white , choose to fine tune the channel. I went up to +17 and the picture became colour \\/


For some reason tvtime is under-tuning the Winfast 2000xp expert tv card. Maybe they can fix it in the future.

---

