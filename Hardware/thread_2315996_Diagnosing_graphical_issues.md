---
title: "Diagnosing graphical issues"
date: 2016-03-04
forum: Hardware
---

### Post by mr-woof on 2016-03-04
Hi all,

about 4-5 years ago I put a new system together comprising of a quad AMD chip and a AS-rock board with Nvidia grahpics on, nothing mind blowing. I always had problems on Linux with the graphics, I've tried different cards and the onboard graphics in Ubuntu especially and it would either 1) Run like a dog or 2) Crash. 

For the last 2-3 years I was using Linux Mint 17 and amazingly it's been fine, but I must of missed an Nvidia update in the list last week and it started playing silly beggars with me again. So I thought it's been a few years since I tried Ubuntu on this machine, maybe the drivers are a bit better etc. I installed Ubuntu Mate 15.10 and it was ok for a bit, but then it crashed. I've been experimenting with the different hardware drivers available and it crashses on each one, the annoying thing it might be 10 minutes or like yesterday it was 7 hours.

This is where my question comes in, I've looked through the log files and I can't see anything out of ordinary (to me anyway). Can anyone suggest anything I can do to see if I can isolate the problem? It's definitely not a hardware issue, overheating issue etc.

thanks all, it's so annoying you wouldn't believe. :)

---

### Post by Bucky Ball on 2016-03-04
*Thread moved to **Hardware**.*

It might not be a hardware issue, as in broken hardware, but it is a hardware issue, if you know what I mean. ;)

Sounds like you have a few cards there. Might be best to let us know what makes/models you have and somebody will probably be able to tell you which have some chance of working and which, if any, aren't worth bothering with. 

Please provide the full specs of the machine you're attempting to get graphics running on. Also, 'it crashed' is not enough information. How exactly, were there any messages, and what did you do to get out of that?

* By the way, have you updated the system and checked Additional Drivers for a recommended driver?

---

### Post by mr-woof on 2016-03-04
Hi,

fair point regarding the hardware issue :) I'll get the Nvidia model when I get back, but in terms of the crash. The screen freezes, you can't do anything apart from holding down the power.

---

### Post by Bucky Ball on 2016-03-04
For the Nvidia, try this.

When you get to the list of OSs at boot, select your kernel but hit 'e' to edit.
Look for the line that ends in 'quiet splash' and add 'nomodeset' to the end of it thus:

```
quiet splash nomodeset
```

Control+x I think to save and continue (but check instructions at bottom of that screen) and see how you go. We can make that permanent if any good because this test only fixes til restart.

---

### Post by mr-woof on 2016-03-04
Hi,

interesting, I've not heard of doing that before. This is a good explanation for anyone else who's never heard of it before:

[http://askubuntu.com/questions/207175/what-does-nomodeset-do](http://askubuntu.com/questions/207175/what-does-nomodeset-do)

I'll give it a go later and see what happens

---

