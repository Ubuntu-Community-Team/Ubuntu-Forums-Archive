---
title: "Driver ebridge already registered, aborting message flooding shell window"
date: 2016-08-15
forum: Hardware
---

### Post by eric112 on 2016-08-15
I recently upgraded to a GTX 1060 and only booted into Ubuntu today, and got stuck in a login loop. I opened a terminal window and updated my Ubuntu version, but still got the login loop. I opened terminal again and the same message kept getting repeated: 
Error: Driver ebridge already registered, aborting...
And something about nvidia nvlink. I can't use the terminal because the message keeps printing. Is there a general way to stop the console from continuously printing?

---

### Post by irvine_himself2 on 2016-08-16
I recognise the error message, as I frequently get stuck in a similar loop during shutdown which necessitates using the power button to fully switch off my laptop. In my case, the problem seems to be related to problems that I am having with udev detailed in [this post]("https://ubuntuforums.org/showthread.php?t=2333906"). Basically, since I became aware of the udev looping problem, restarting udev appears to solve my shutdown loop problem. How to check whether this is true or not, is way above my pay-grade though.

As far as your immediate problem is concerned, [this post]("https://askubuntu.com/questions/774398/cant-boot-into-ubuntu-after-installation-of-nvidia-driver") may be helpful.

Good luck
Irvine

---

### Post by eric112 on 2016-08-16
Will purging Nvidia settings from Linux also remove them from my Windows partition?

---

### Post by howefield on 2016-08-16
> **eric112 said:**
> Will purging Nvidia settings from Linux also remove them from my Windows partition?

No. 

The commands will only have effect on your Ubuntu installation.

---

