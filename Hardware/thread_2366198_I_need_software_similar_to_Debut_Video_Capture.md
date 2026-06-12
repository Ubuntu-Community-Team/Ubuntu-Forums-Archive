---
title: "I need software similar to Debut Video Capture"
date: 2017-07-14
forum: Hardware
---

### Post by rustindirt on 2017-07-14
I have two EasyCap´s (USBTV007 & 534d:0021 <Doesn´t have a  name, says EasyCap on the plastic>) But when using VLC, I could never get any sound through any of the  EasyCap´s, even with Line In or Mic In.

Specs:
Processor - AMD Athlon64 X2 Dual Core Processor 5000+
Memory - 1799MB (886MB used) 
Operating System - Ubuntu 16.04.2 LTS
Graphics (Intergrated) - GeForce 6150SE nForce 430

---

### Post by Bucky Ball on 2017-07-15
These are for watching TV? If so, I use an Easycap and use MeTV. You'll find it in the repositories (Software). It has the advantage of being able to do an auto-scan to pick up channels in your area so you don't need to use a channels.conf file. It creates one for you.

There are a few different Easycaps, but mine works out of the box in 16.04 LTS.

(PS: Is this a straightforward USB dongle that plugs directly into the computer? Like I said, there are few different Easycaps, so sorry if I'm off the mark. Your audio problems, incidentally, may be a matter of experimenting with Pulseaudio Volume Control (you can also install that from the repositories. ;))

---

### Post by rustindirt on 2017-07-16
Yes, I know that I am running an old version of Ubuntu. Ubuntu 16:04 runs terribly on my machine. 


So I have two EasyCaps: 


534d:0021 - Unknown (Says EasyCap on the plastic)
1b71:3002 - Fushicai USBTV007


I've looked around and have no clue if any of these EasyCaps work in 12.10, I don't want to risk bricking my system.


I have checked here:
[https://linuxtv.org/wiki/index.php/Easycap#USBTV007_EasyCAP](https://linuxtv.org/wiki/index.php/Easycap#USBTV007_EasyCAP)


But I really don't have a clue how to install the driver, or even if it is compatible.


Thanks, RustInDirt

---

### Post by Autodave on 2017-07-17
I did a quick search and at least the Fushicai should work with Ubuntu, but not with your old version.  What are the specs on your machine?

Perhaps you need to look at a different version like Xubuntu or even Lubuntu. Ubuntu is a very heavy desktop and uses a lot of resources. I run Xubuntu 16.04 on a single core, 900mhz netbook with no probs at all.

---

### Post by slickymaster on 2017-07-17
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by Bucky Ball on 2017-07-18
You might be better off posting a thread about the problems you are having with 16.04 LTS and trying to get that working. 12.10 is ancient and you really will be struggling to get much help with it. Not much point asking if your Easycap works with 12.10. Of the few of us who have that device, very few would remember much about 12.10, if they even used it (for instance, I didn't).

It is a policy of Canonical not to give support for EOL releases. The forums don't 'officially' support EOL releases either, but good luck. The info you found online and elsewhere so far, and it looks like you've had a good dig, might be about as good as it gets.

On the other hand, we can certainly help you with installing 16.04 and getting that up, in which case you can then just plug the device in and get on with what you want to do. (Incidentally, 16.04 LTS is a long-term support release, supported for five years until 2021. ;))

---

