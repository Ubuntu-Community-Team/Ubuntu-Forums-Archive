---
title: "So where do we stand with the touchpad problem?"
date: 2009-12-11
forum: Hardware
---

### Post by thered on 2009-12-11
I've posted before in other threads on this subject. Reading other threads, there is obviously a problem with the detection of touchpads, seemingly both ALPS and Synaptic.

I'm running an Acer Aspire 5738z and I'm totally frustrated at not being able to turn on " Disable while typing". I've got a fresh install of 9.10

I've read most, if not all, the threads highlighting the problem.  There maybe an answer to the problem by hacking the kernel :shock:!

Well I don't mind a bit of CLI but baulk at anything more - "Linux for Humans" is my motto.

So, my question, is it possible to detect the driver? is it possible to get gsynaptic to run? how long before the problem is resolved?

I think, with the price of your average laptop today means a bigger uptake in ownership that the priority of this problem is increased.

[BTW - the "disable while typing' problem has manifested itself three times while typing this missive] :(

---

### Post by nomadluap on 2009-12-21
same problem here, bro.

---

### Post by Nuzgal on 2009-12-21
I have the same laptop as you do. 
However, I've managed to solve this problem by using the 
```
modprobe -r psmouse
``` 
(this removes psmouse module - disables mouse)
and when I want to use touchpad again I just 
```
modprobe psmouse
```

---

### Post by nomadluap on 2009-12-21
That may work, but I think what thered is referring to is the fact that there is no touchpad tab in the mouse preferences. I opened a new topic about it, [http://ubuntuforums.org/showthread.php?t=1361031](http://ubuntuforums.org/showthread.php?t=1361031)[http://ubuntuforums.org/showthread.php?t=1361031]("http://ubuntuforums.org/showthread.php?t=1361031")

---

