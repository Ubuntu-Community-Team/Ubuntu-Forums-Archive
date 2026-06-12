---
title: "Dell Inspiron Cannot Detect Discrete Graphics Card"
date: 2011-10-02
forum: Hardware
---

### Post by zenben1126 on 2011-10-02
Hello, 

I'm running a Dell Inspiron N5110 with two graphics cards: Intel and AMD Radeon. The problem is that in order to run more advanced graphical processes, I need to enable the discrete video card (AMD Radeon HD xxx). I have tried to use switcheroo to change between the two graphics cards, but with no success because for some reason my computer can't detect the AMD card at all...


The output for 
**lspci -vnnn | grep VGA**
is as follows: 
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
```When I run switcheroo in an interfaced version found [here]("http://asusm51ta-with-linux.blogspot.com/"), the window that pops up properly identifies my Intel card but not the discrete one...

Output as follows: 
```
Choose Hybrid Graphic Card
=================
Integrated:  : Intel 2nd Generation Core Processor Family 
Discrete:  : 
```I have been trying to solve this issue for MONTHS and would greatly appreciate some assistance! I'm using all stock hardware, and am running ubuntu natty 11.4 64-bit.

---

### Post by altometer on 2011-10-02
[http://ubuntuforums.org/showthread.php?t=1853167](http://ubuntuforums.org/showthread.php?t=1853167)

Do a search before posting. :P There are some problems but it works pretty well.

---

### Post by zenben1126 on 2011-10-03
I installed the driver and cant run the aticonfig at all. I've been researching this for months and to no success. Sudo aticonfig tells me i have no available adapters.

---

### Post by altometer on 2011-10-03
I had that issue, you need to reboot and install it again. You may need to install it by bash only. Log in via pressing alt+f2 and install from there.

---

