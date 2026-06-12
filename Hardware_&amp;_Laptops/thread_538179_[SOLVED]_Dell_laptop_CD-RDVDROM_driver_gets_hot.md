---
title: "[SOLVED] Dell laptop CD-R/DVDROM driver gets hot"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by tak1150 on 2007-08-29
I have a Dell Inspiron 1150 with Ubuntu 7.04 on it and this laptop gets really hot (72-4 C) even when idling.
I checked the processes with "top" command and it seems like beagled is doing some work, but not much.

It seems that a lot of heat is coming from both the CPU and the CD-R/DVDROM drive. CPU, I understand. But why does my DVDROM drive get hot :confused:

I have cpufreq-selector and computer temperature monitor set up so that when the CPU temp gets to 73C, CPU switches to 1.6GHz instead of "ondemand" mode which often gets the CPU frequency to 2.8GHz (when idling!).

I vaguely remember that Edgy didn't do this. So I'm thinking that it has to do with Feisty (kernel)??? Thanks for your advice / tips /help!

Tak

---

### Post by tak1150 on 2007-09-11
Since this post, I got **gkrellm** and the CPU temp is very well regulated by the fans.
The temp of the CD drive is still HIGH. so this means that it really has something to do with the CD drive and not the CPU temp.

Any help is appreciated!

---

### Post by tak1150 on 2007-09-12
I have confirmed that the source of the heat is the wireless card.
I will mark this as solved and open [a new thread]("http://ubuntuforums.org/showthread.php?p=3354616#post3354616").

---

