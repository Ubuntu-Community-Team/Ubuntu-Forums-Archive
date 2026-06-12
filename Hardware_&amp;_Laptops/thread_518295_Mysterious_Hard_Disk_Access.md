---
title: "Mysterious Hard Disk Access"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by pepebe on 2007-08-05
Oh happy day!

I have finaly succeeded to install ubuntu 7.04 on my acer extensa 3000.

I was able to solve all initial problems (screen, grafic card, wlan, keyboard) and now everything SEEMS to work fine. 

Yet, there is something that makes me a bit nervous. On winXP I usually don't hear the laptop at all. On ubuntu every 2 or 3 seconds something is accessing my harddisk for about one second. This also havens, if I do nothing at all...

It's driving me crazy!

Because the whole Linux/Ubuntu thing is still new to me, I'm not sure how to find the task or application causing that behaviour.

I would be very grateful, if something could pinpoint me to the right tool to find out what's going on or give me an explanation for this.

Greetings,

pepebe

---

### Post by nick_h on 2007-08-05
From the terminal the commands you need are *ps* and *top*.

To see all processes running type:
```
ps -ef
```
To see in a table the process consuming most cpu type:
```
top
```
You could also install htop if you like top.

---

