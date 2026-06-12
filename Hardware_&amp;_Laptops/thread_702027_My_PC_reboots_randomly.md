---
title: "My PC reboots randomly"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by victorllorens on 2008-02-19
Hello,

can a corrupted filesystem make a system reboot randomly?

I'm working as always and suddenly my pc reboots, or my ubuntu freezes (the keyboard leds blink, kernel panic?) .

Then when I reboot and ubuntu loads, fcsk says Filesystem is not clean.

It's strange because i have just installed it two days ago! But I have had those insane reboots for a long time... maybe I should change my pc...

Thanks in advance

---

### Post by Existentialist on 2008-02-19
It could also be caused by overheating, or a bad power supply.  Did it ever reboot while you were installing or using the live cd?  If so its probably not the hard drive and you will want to look at other components as the source of the problem.  If not you could try running it off of the live cd, or running memtest86+ to check if its a hardware issue, otherwise it is most likely the hd which sounds most likely.  You may just need a new hd which doesn't sound too bad if you just installed a couple days ago.  Probably not that much data to back up yet.

---

### Post by victorllorens on 2008-02-19
It did not reboot while installing ubuntu (I think I was lucky ...), but it did while I was installing windows.

Yesterday I started memtest before go bed, and got asleep T_T. This morning was still doing memtest, so I assume RAM passed memtest and not only one :D.

Temperature is ok. Alls fans are working, and I cleaned all pieces including power supply internally.

It seems HD, CPU, Motherboard or power supply. But I wanted to know if the reboots are caused by a corrupted filesystem too (in that case we would have 2 or more causes and we want only one) .

I'm not used to looking in linux logs, but I have tried looking in /var/log but found nothing special.

Thanks.

---

### Post by Existentialist on 2008-02-19
So it says your filesystem isn't clean, even after a proper shutdown and boot up?  Have you ran any hard drive tests in windows or checked what SMART is saying?  I know a program called hdtune in windows can read SMART values to tell you if there are errors and run a disk check.  I'm sure there is comparable linux programs, but I've always liked hdtune.

[http://www.hdtune.com/](http://www.hdtune.com/)

---

### Post by victorllorens on 2008-02-19
Ok thanks, I will swap to windows and try that. Let's see :)

---

### Post by oldsoundguy on 2008-02-20
when you come back, that is a symptom of an INSUFFICIENT power supply also.  If you have added more fans and additional hardware recently, that could be the cause.

---

### Post by Wiebelhaus on 2008-02-20
Lets start with the basics people , what's the most common reason this would happen?




A failing hard drive , download HDD diags and run the extended test and ensure a SMART (Self Monitoring and reporting technology) status check.

Then move onto Ram Diags and ensure your using a Battery back up device to eliminate the possibility of a failing power supply , if you do all these things and the issue still persists then start diagnosing the complicated or irritating things like thermal and PSU failures and so on.

---

### Post by jblackthorne on 2008-02-20
Ubuntu has SMART tools as well.  

sudo apt-get install smartmontools

Then run:

Run, sudo smartctl -A /dev/sda

This article does a great job of explaining what the values mean:

[http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/](http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/)

---

### Post by victorllorens on 2008-02-20
> **Existentialist said:**
> So it says your filesystem isn't clean, even after a proper shutdown and boot up?  Have you ran any hard drive tests in windows or checked what SMART is saying?  I know a program called hdtune in windows can read SMART values to tell you if there are errors and run a disk check.  I'm sure there is comparable linux programs, but I've always liked hdtune.

[http://www.hdtune.com/](http://www.hdtune.com/)

It says my hd health was ok. No problems in pc health tab.

> **sx66gns said:**
> Lets start with the basics people , what's the most common reason this would happen?

A failing hard drive , download HDD diags and run the extended test and ensure a SMART (Self Monitoring and reporting technology) status check.

Then move onto Ram Diags and ensure your using a Battery back up device to eliminate the possibility of a failing power supply , if you do all these things and the issue still persists then start diagnosing the complicated or irritating things like thermal and PSU failures and so on.

SMART reports are ok, memtest are ok, temperature is ok. As oldsoundguy sayd, that issue is starting to point to major problems...

A lot of friends say it's the power supply, but i keep saying no (maybe im incorrect) because in windows it simply reboots but in linux (debian and ubuntu) it usually leaves the pc like in kernel panic (very few times reboot).

Tomorrow I buy a new PSU if nothing brilliant happens before :frown:

Thanks to all again friends

---

### Post by oldsoundguy on 2008-02-20
a follow up, I had a box that was running windows .. it would re-boot by itself all the time and I would lose the wireless.  When a lot of OTHER Windows issues came up, I decided to try and Ubuntize it.  When I tried to load the system it dumped .. several times.  Pulled the power supply, put in a bigger one, and I am writing this ON that computer.

---

### Post by victorllorens on 2008-02-20
Yes I agree with you, but I will go buy one without knowing if its exactly the problem... I hope I have the same LUCK as you ;).

The only positive thing will be that i will have 2 redundant PSU.

btw I bet: 50% PSU, 30% Motherboard, 20% CPU. I will keep this thread alive while pc reboots. 

Thnx.

PS: 1 hour rebooting and testing HD and it has not rebooted/freezed yet!

---

### Post by victorllorens on 2008-02-24
With my friend's PSU still was rebooting/freezing. 

I upgraded the BIOS like 5 versions and now it works fine, well at least it is on since Friday.

I figured it out when I putted RAM in single channel and ubuntu freezed just in 3 seconds of booting.

:lolflag:

---

