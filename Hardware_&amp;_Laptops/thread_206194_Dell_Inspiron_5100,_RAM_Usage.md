---
title: "Dell Inspiron 5100, RAM Usage"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by mishranurag on 2006-06-29
I noticed in K SysGaurd that the RAM used by my system is around 350Mb, and I haev around 384 Mb. It stays like this whether the computer is sitting idle for long time. Currently I am writing on another computer and see laptop usage as following. I have not touched it for at least 15 minutes

CPU - less than 10%
Physical Memory (RAM) - around 350 MB of 384 MB
SWAP - almost zero of 1 GB 
temperature, I just checked 59C (it is same for last 15-20 minutes)
fan speed, I guess is low.

Are these numbers normal?

Thank You
Anurag

EDIT: Forgot to add, no application is running!

---

### Post by Hellkeepa on 2006-06-29
HELLo!

The CPU usage, and temp, is not quite normal. There's a bug in the -686 (SMP) kernel, and the circumstanes around it are explained in this thread (and it's linked post):
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

As for the memory; That might very well be normal, as X does require quite a bit of memory. Linux also chaches stuff into the RAM, to give you a better response time. Unlike on Windows, and this actually works.
It's when your SWAP is starting to get used when you should be raising an eyebrow, and keep monitoring your RAM usage. ;)

Happy codin'!

---

### Post by mishranurag on 2006-06-30
I have a 386-kernel now.Should I go aheand and install 686 kernel? If yes, exactly what things I need to install?

Thanks
Anurag

---

### Post by Hellkeepa on 2006-06-30
HELLo!

First off check what the content of the four files mentioned in my thread is, and if you can spot any issues in them.
Also, please make sure that you are in fact running the -386 kernel, by using the "uname" line provided in that thread. I thought I was running the .12-686 version, when "uname" showed me that I was indeed running the .25-686 version, so you never know. ;)

Happy codin'!

---

### Post by mishranurag on 2006-07-03
Sorry to reply two days later, but my system does use 2.6.15-25.386 kernel! That means my CPU should not have any problem. Should  I install 686 kernel or I should not bother about it?

Anurag

---

### Post by hizaguchi on 2006-07-03
You can open a terminal and type "free -m" to get your actual memory usage.  It'll spit out 3 lines of info.  The first is the amount that's being cached (as was mentioned above), but the second and third are how much memory is actually being used by the programs you're running.  That's what's important for performance.

---

