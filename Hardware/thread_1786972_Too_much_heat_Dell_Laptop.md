---
title: "Too much heat Dell Laptop"
date: 2011-06-20
forum: Hardware
---

### Post by najdorfchess on 2011-06-20
Hi all. I have been experiencing this problem in my laptop ever since I installed Ubuntu linux. I find that my laptop gets too much heated up when i use Ubuntu rather than the recommended OS viz., Windows 7. All the external areas including the plastic back, the touchpad and even some of the keys get very hot which makes it tough to use for long hours. I would like to know what could be the possible reason for this scenario? I use it in Air conditioned room under normal temperature (atleast most of the time). 
I didn't install any external driver except for the wifi driver. And I use power management option that's set default.


Specifications of my laptop
===========================

Dell Inspiron 15R 
Core i3 370 series processor
4GB RAM
Ubuntu 11.04 64-bit
Have given a swap space of only 1GB since I thought 4 GB is sufficient enough.

PS. My apologies if this has been asked before several times.

---

### Post by najdorfchess on 2011-06-20
One more general query regarding the forum. How could we see our personal posts/ threads? I tried searching for the link in User CP, but I'm unable to find it. Thanks :)

---

### Post by dFlyer on 2011-06-20
> **najdorfchess said:**
> One more general query regarding the forum. How could we see our personal posts/ threads? I tried searching for the link in User CP, but I'm unable to find it. Thanks :)

First install lm-sensors to check your temp. To find your threads just click search, than find your threads.

---

### Post by najdorfchess on 2011-06-20
Thank you for ur reply, how could i do that?

---

### Post by dFlyer on 2011-06-20
Start Synaptic package manager. Under filters enter lm-sensors. If not installed right click it and mark to install, press apply. From the command line enter:

sensors -f    press enter

---

### Post by najdorfchess on 2011-06-20
Okay I just did that. Here is my reading 

[I]acpitz-virtual-0
Adapter: Virtual device
temp1:      +146.3°F  (crit = +188.6°F)   
[/I]
Even though it hasn't reached a critical state I still believe this is a high temperature. Any suggestions to bring it down? Also I can hear my fan in full swing.. So that shouldn't be an issue.

---

### Post by c2tarun on 2013-01-13
Hi sorry for replying for in such an old and Solved thread.
I installed Ubuntu 12.04 and my laptop started heating too much. Then I found this link: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513)


After installing latest graphics drivers system temperature improved considerably. Fan is running slow, laptop is not heating up much. I'll suggest everyone with ATI graphic card to follow the steps and install latest driver provided by ATI.

---

### Post by overdrank on 2013-01-13
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

