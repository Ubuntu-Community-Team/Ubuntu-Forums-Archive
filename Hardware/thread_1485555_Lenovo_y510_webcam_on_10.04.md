---
title: "Lenovo y510 webcam on 10.04"
date: 2010-05-17
forum: Hardware
---

### Post by river16 on 2010-05-17
Hello, I'm running the latest (10.04) version of Ubuntu on a lenovo Y510 laptop. I have most everything working except the webcam. From reading older threads, it seems like most y510 webcams work out of the box with older versions of ubuntu. Is it just the new version? If anyone could help me get this running, I would greatly appreciate it.

Thanks
~river16

---

### Post by ninoy_arnaldo on 2010-05-26
not my case. seems to work in my box.

---

### Post by innerwolf on 2010-09-28
My webcam is also working out of the box. It is usually the sound and the front mic that give problems.

check your settings:

In terminal:

:~$ gstreamer-properties

and under Video try to test with v4|2 and v4|

---

### Post by innerwolf on 2010-09-28
Also... don't forget that there is a hot key for the webcam on this laptop! Did you check that? Fn+Esc might solve your problem :)

---

