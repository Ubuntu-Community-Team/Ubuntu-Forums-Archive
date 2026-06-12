---
title: "Acer 5535 - fans and overheating issues"
date: 2014-02-24
forum: Hardware
---

### Post by rachel-g41 on 2014-02-24
First, not sure where to put this, Mods feel free to move it.

Yesterday I installed lubuntu on an Acer Aspire 5535 - reformatting and removing Windows.

It appeared to run fine at first but then shut down a couple of times making me suspect overheating. So I googled, and founds lots of info about overheating problems with this series. 

Comments/suggestions include updating BIOS, the fact that acer fans are controlled by acer e-management within windows so don't work in Linux. There are some suggestions but they look scary to a new user and the threads are on the whole quite old.

I've looked at threads regarding use of lm-sensors, x-sensors etc

I now have 13.10 32-bit running and while the temp is high, it's running ok.

However, while trying some of the suggestions I've found that

(1) xsensors cannot see a fan. It's as though the fan isn't there. It gives me 3 temps but nothing else.
(2) pwmconfig says there are no pwm controlled devices
(3) My BIOS version appears to be the same (1.04) as the most recent listed on the Acer site for this machine so while some users found updating the BIOS to solve the problem, I'm not sure that'll help me

Today I found this thread [http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521)

Is this likely to be the answer? *(there is a comment later on that says it doesn't work on 13.10 but I haven't tried it yet)*

Many thanks for any thoughts.

---

### Post by mörgæs on 2014-02-24
'Hardware' is a fine place for the thread. 

One of the most common problems with used laptops is dust accumulating in fan and heat sink, plain and simple. Often there are instructions on Youtube describing how to take the casing apart and clean the interior.

---

### Post by Yellow Pasque on 2014-02-24
So is the fan not functioning correctly (i.e. when the CPU is getting hotter, does it not spin up)?

> (1) xsensors cannot see a fan. It's as though the fan isn't there. It gives me 3 temps but nothing else.
(2) pwmconfig says there are no pwm controlled devices

Those are more for desktops. Laptops use ACPI to control their fan.

> Acer Aspire 5535
If it has the RadeonHD 3200 GPU (check output of lspci if not sure), then try enabling dpm: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

> One of the most common problems with used laptops is dust accumulating in fan and heat sink, plain and simple. Often there are instructions on Youtube describing how to take the casing apart and clean the interior.
If one is going to take apart the laptop for cleaning, it would probably be a good time to redo the heatsink paste. Laptop manufacturers often use cheap thermal pads that degrade after some years.

---

### Post by rachel-g41 on 2014-02-24
Thanks both for the replies and thanks Temüjin for clarifying the use of those utilities. 

I can't hear the fan, previously (with Vista) it was quite noisy. I realise that might be an improvement as the point of switching OS was that the machine was working far too hard and slowly. I will (try to) open it up and give it a clean; I downloaded the manual yesterday and it looks straightforward so long as the screws come out easily.

There may be nothing to worry about, maybe reading those threads was the equivalent of reading a medical dictionary and coming to the conclusion that I'm dying. I will try not to worry so much and watch to see how it goes over the next few days.

Thanks again for taking the time to reply.

---

### Post by Yellow Pasque on 2014-02-24
> maybe reading those threads was the equivalent of reading a medical dictionary and coming to the conclusion that I'm dying.
No, that was good googling. If it's shutting down from overheating, something is definitely wrong.

---

### Post by rachel-g41 on 2014-02-24
Thanks - it hasn't shut down today. Yesterday I started with 13.04 - today I reinstalled to get 13.10 and made sure to get 32bit.

xsensors is giving me acpitz 73/66 ºC currently. The fan kicked in when that top temp got to 80ºC, temp dropped and now appears to be steady. 

Does this sound ok?

---

### Post by Yellow Pasque on 2014-02-24
It seems the fan control algorithm is still a bit off.  While it's far from ideal to have your processor idling at 73C, the fact that it runs full blast at 80C is reassuring, since the CPu is rated to run to 95C [http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20TF-20%20-%20AMGTF20HAX4DN.html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20TF-20%20-%20AMGTF20HAX4DN.html)

---

### Post by rachel-g41 on 2014-02-24
Thank you, I'll try not to worry about it then. 

Is there anything I can/should do about the algorithm?

---

### Post by Bucky Ball on 2014-02-24
All good, but compressed air and another fix were suggested on the other thread you posted about this and you did not reply about the results of either, here or there. :-k

[http://ubuntuforums.org/showthread.php?t=2206601&page=3&p=12938583#post12938583](http://ubuntuforums.org/showthread.php?t=2206601&page=3&p=12938583#post12938583)

---

### Post by rachel-g41 on 2014-02-25
I haven't got compressed air yet - I mentioned on the other thread that I  might not be able to get it locally and it would have to wait untl today (or tomorrow). I still intend to open it up and clean it when I get time, again hopefully today or tomorrow.

The other fix, I'm not sure that's my problem. Is it? I will have a look after work today. 
 
So far though, things seem to be going well.

---

### Post by mörgæs on 2014-02-25
Compressed air is easy to use, but it does not always solve the problem. If the dust/hairball has 'hardened into a solid mass' then it's better to take the casing apart.

---

### Post by rachel-g41 on 2014-02-26
At the second attempt I managed to get the laptop open and it's had a good clean. It was pretty dusty in there but it's back up and running now. The temperature hasn't changed that much but as the days go by with no shutdowns and the fan coming on consistently at 80ºC, I feel much happier. 

Thanks again for all the help and advice.

---

### Post by mörgæs on 2014-02-27
Good, please mark the thread 'solved'.

---

