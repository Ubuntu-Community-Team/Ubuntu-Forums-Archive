---
title: "Laptop-mode not running in Ubuntu 9.04"
date: 2009-09-02
forum: Hardware
---

### Post by xtremethegreat1 on 2009-09-02
I have a laptop. I was checking out this laptop-mode-tools website today. Then there was this line:

> How do I check if laptop mode is enabled?

Execute cat /proc/sys/vm/laptop_mode. If it contains a nonzero value, then laptop mode is enabled, if it says 0, then it isn't.

I tried to cat out that file, but it says 0. I checked to see that I have laptop-mode-tools package installed. Can someone help regarding how to enable this? Because I tried /etc/init.d/laptop-mode start, but it was still 0.

Please note that all commands were executed as root. So, privileges was not the problem.

---

### Post by kevinatkins on 2009-09-02
Hi,

Even if you have laptop-mode-tools installed, it isn't enabled by default. See this link for details of how to enable laptop mode -

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Useful_Task:_Enable_Laptop_Mode]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Useful_Task:_Enable_Laptop_Mode")

I've tried the various laptop mode scripts and found things to be a little buggy, to say the least - YMMV. Still, it's worth trying - I'm assuming you're hoping to extend battery life, etc. It would seem from my 'Googling' that some laptops respond better than others.

---

