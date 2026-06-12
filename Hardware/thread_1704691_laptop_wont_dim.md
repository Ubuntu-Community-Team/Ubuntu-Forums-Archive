---
title: "laptop wont dim"
date: 2011-03-11
forum: Hardware
---

### Post by AnnAni1234 on 2011-03-11
I have a dell inspiron 1525 and when i am trying to dim the light it isnt working the brightness stays full even though the indicator shows that it is going down.

please help i have attached pics

thank you

---

### Post by kcxzero on 2011-03-11
This isn't a solution to the brightness level issue in your screen shots [http://ubuntuforums.org/showthread.php?t=1702863](http://ubuntuforums.org/showthread.php?t=1702863) but if you want to use it while waiting for a response from someone else, you're welcome. It will "dim" your monitor but it isn't the most convenient way of doing it. I'm using a vaio and as far as I know there isn't a full solution to this problem for my system. However, there should be one for yours.

---

### Post by Zevaka on 2011-03-11
hello
as temporary fix you can try
sudo setpci -s 00:02.0 F4.B=**XX**
here, **XX** is level of brightness in HEX (from 00 to FF), never set :)
if you want this automated, check this post:
[http://ubuntuforums.org/showpost.php?p=10108048&postcount=36](http://ubuntuforums.org/showpost.php?p=10108048&postcount=36)

---

