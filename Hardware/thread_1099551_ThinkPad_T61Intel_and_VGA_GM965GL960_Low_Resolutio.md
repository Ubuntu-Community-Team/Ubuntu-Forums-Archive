---
title: "ThinkPad T61Intel and VGA GM965/GL960 Low Resolution Display"
date: 2009-03-18
forum: Hardware
---

### Post by tzury on 2009-03-18
Running Ubunti Intrepid Ibex (8.10)

My VGA details:

```
tzury@thinkpad:~$ lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

My screen resolution can only display 1024x768 at most. It should be higher than that as it was in the previous OS (Windows).

---

### Post by Hoppiesbox on 2009-07-16
Same issue here. While plugged into a secondary display windows will run both displays at their maximum resolution (1024x768 on the laptop, 1280x1024 on the second display). Under Ubuntu though it's creating a single virtual display of 2048x768.

---

