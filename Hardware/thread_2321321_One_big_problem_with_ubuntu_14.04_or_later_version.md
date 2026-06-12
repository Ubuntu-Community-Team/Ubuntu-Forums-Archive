---
title: "One big problem with ubuntu 14.04 or later versions"
date: 2016-04-22
forum: Hardware
---

### Post by zhang_sir on 2016-04-22
My laptop is hasee K470p i7 d2 .CPU-i7 2670qm, chipest- intel HM65 seriels,GPU-amd radeon hd 6770m
ubuntu 13.10 and older versions can be installed on my laptop successfully and everything is OK.But 14.04 or later cannot.The problem is that my laptop suspend its all work to RAM even from the process of installing per 30 seconds (approximate) and it goes on installing after I pressed the power button.The same problem is there after the installed OS starts.
I have tried other OS such as fedora&#12289;debian and centos .The same situation comes there.
SO I post it here and I need your help. Thanks a lot if you can give me some advise.

---

### Post by Bucky Ball on 2016-04-22
Sorry, but don't understand the issue you're having installing. 
> 
The problem is that my laptop suspend its all work to RAM even from the process of installing per 30 seconds (approximate) and it goes on installing after I pressed the power button.

? Could you be a bit more specific? How exactly is the install failing? Error messages?

---

### Post by zhang_sir on 2016-04-22
Actually,the OS can be installed and started.But in the process of installing the laptop itself often suspend,there&#8216;s nothing showing on the screen.It just suddenly suspend(Only RAM works) I need press the power button in order to go on the installing.The OS can be installed in this situation.The same question comes when the OS starts desktop.

---

### Post by Bucky Ball on 2016-04-22
Can't you get to a screen again and see the progress of the install by hitting the space bar?

Not sure you have a problem if the OS is installing fine and everything is running as it should apart from this. There may be times when the screen needs to go off during install, the screen could simply be going into screensaver/power saving mode. If you hit a space bar and everything is still purring away, nothing to worry about.

---

### Post by zhang_sir on 2016-04-22
It is not power saving mode.It suspend all work to RAM(cpu,screen and hardrive all stop ,only RAM works.) I can see it from the indicator light. It does not work if I hit space bar .It only works after I hit the power button.

---

### Post by Bucky Ball on 2016-04-22
Still not quite getting it. So ...

1/ You've installed Ubuntu?
2/ When you are using Ubuntu the computer suspends to RAM after 30 seconds and you get a black screen?

Am I close? And lastly:

3/ Have you tried another flavour of Ubuntu (Xubuntu or Lubuntu perhaps) to see if that gives the same result?

---

### Post by zhang_sir on 2016-04-22
That's right about what you're thinking now. I've tried ubuntu 14.04 or newer,fedora 21,debian 8.4 and centos. This problem also exists there.
The bootable media (USB) is OK. I've tried it on another PC. Everything's fine on the PC.

---

### Post by sgian on 2016-04-22
I tried researching this graphics card, and have found complaints about it with linux.  To eliminate your graphics card as a possible reason for your troubles with linux, try removing the graphics card and then installing Ubuntu 14.04 or 16.04.  That should work.  If it does work, then you'll know that the graphics card is not well supported in linux.  If you install 16.04, keep in mind if you get another graphics card that AMD has issues with 16.04 until possibly this summer so in the short term you might want to consider NVIDIA until the AMD driver issue is sorted out in 16.04.

---

### Post by zhang_sir on 2016-04-22
Thanks for your advice. I plan to do it like what you say. I'm afraid it doesn't work.

---

