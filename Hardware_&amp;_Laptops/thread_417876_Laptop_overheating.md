---
title: "Laptop overheating"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by powaz on 2007-04-22
Hi:

My laptop seems to be overheating when the processor is at work, which results in an automatic shutdown. This started happening within the last month and a half while I was using edgy but happens consistently now on feisty. I've done some checking around and all signs allude to a bug in the version of the kernel used by feisty. Don't quite remember if the problems on edgy started after I upgraded the kernel. I hope someone can shed some light on this, it's a really BIG inconvenience to say the least, it's preventing me from doing my work and I'd hate to switch from categorically the best linux distro out there to something else.

My laptop is a dell precision M70, 1G Ram, 2.0 CPU . I ran the dell diagnostic tool and everything seems to be ok with the hardware. I also went ahead and upgraded the BIOS, still nothing.

Any help at all (except go back to windows) will be appreciated.

Thanks.

---

### Post by powaz on 2007-04-24
Called in Dell, they changed my motherboard and now everything is ok.

---

### Post by mikedeaton on 2007-05-01
Hah, do you know if they swap out parts in laptops? Like if I call and tell them I wanna upgrade my video in my laptop from a ATIx1300 to a x1400? and my processor to 1.8 duel core.

---

### Post by flightless bird on 2007-05-10
I am having an identical problem with my HP ze4315 under Feisty. It worked fine until I installed the updates and now it consistently shutsdown within a minute or so of startup saying that I have passed a critical temperature of ~40C.

---

### Post by Marvelboy on 2007-05-15
I've been having problems with my HP laptop as well, exactly as the person above me stated.  When the kernel updated my computer began overheating.

Any help on this would be appreciated, my windows friends laugh at me that Linux is killing my computer :(

---

### Post by helgi on 2007-05-15
I have the same problem with over heating. Installed xubuntu 7.04 a few days ago. Have an HP nx900 laptop. Get system kill when temp 40c<

---

### Post by jamieplucinski on 2007-05-15
Same problem, right now I am supposedly running at 60C when in reality it's ~25 degrees less.

---

### Post by Bablefish on 2007-05-15
Sometimes Laptops just plain overheat for no good reason. I heard of this cooling pad the runs right off the USB port, why don't you give it a try.

---

### Post by helgi on 2007-05-15
This problem actually started after I patitioned my hard drive with Partition Logic(partitioning in the xubuntu setup didn't work). So the problem started happening as I was in the Xubuntu Setup. I had to make like 6-7 tries before I actually got through the setup without the system being killed.

So my hard drive was blank as the problem started to occur(i.e. no operating system in place at the time)

---

### Post by Marvelboy on 2007-05-17
I understand that laptops can overheat for no good reason, but 2/3 of the time when i watch a youtube or flash video my laptop shuts down because of overheating.  This is almost a daily occurance.  This did not happen a few months ago.

---

### Post by atlfalcons866 on 2007-05-17
i am no laptop expert but maybe you should check your thermal paste on the heatsink?

---

### Post by timetravel on 2007-05-18
Try iTray cooler, I got it ebay.

My laptop only has a scrawny 512 RAM (PC2700), shared graphics, 400Mhz FSB.  It use to just get really hot and grind to a stop, freezing in the middle multiple apps. It was outta warranty anyway, so I could'nt send it in for testing. I was looking for a USB fan cooler on ebay, as suggested, but found this power free cooler. 

I got it because it had thermograph proof and so far so good.  I can watch stuff on Youtube, Dailymotion while running spreadsheets, emails, all at the time without overheating.

I tried to push it to the limit, watch DVDs while running virus scan at the sametime, in bed, on the couch etc, no problems! Cheaper than upgrading.

---

### Post by rcsarver on 2007-06-20
Same problem with HP laptop overheating. Never had the problem before feisty.

---

### Post by jcankrom on 2007-06-22
I have a similar problem with my HP ze4315. I haven't had it overheat while running, though it does seem hotter than it did in XP and I havent had much time to use anything with 3d graphics lately. it has "overheated" on a cold startup: reads the temperature sensors at 120C and shutsdown automatically. its only done this to me twice so far, but since last night was the second time, i may have more to discuss . . . 
Jeff

---

### Post by reset3x on 2007-06-22
I'm not sure if this pertains to anyone else but I fixed this by pulling the heat pipe out of my Toshiba and vacuuming out the dust... I cleaned the the cpu and heatsink with rubbing alcohol and applied some Arctic Silver... No problems since....

---

### Post by BatteryKing on 2007-06-22
I purchased a Core2 based laptop several months ago and immediately installed Ubuntu on it (6.06 initially) and have been keeping it up to date (now on 7.04 Feisty Fawn).

When I fist manually set up power management under 6.06 it worked fine, but in a few months while under 6.10, it started having overheating problems and got worse over time even with 7.04 Feisty Fawn installed.  Something very basic came to mind to fix the problem:

SOLUTION: Blow the dust out of the vents (with air compressor or can of compressed air) every few months under 1/3 day use on average.

With this solution now my notebook works great and does not overheat.  I believe the reason for this is with smaller vents and more air being blown through those vents, they just clog up quicker.  Plus it seems Ubuntus's power manager for Intel based notebooks a little is less robust than Windows XP, so you will see heat related problems under Ubuntu first at the time of this writing in a default setup.  (Unless of course someone can show me manual tweaks that will get me on par with Windows XP power management.)

By the way the combination of upgrading to 7.04 Feisty Fawn and blowing out the vents fixed all of the major usability problems I was having with my Gateway NX860XL notebook under Linux, making Linux on a notebook a rather enjoyable experience for me now.

---

### Post by glorytoad on 2007-08-03
I've got a Toshiba portege laptop running standard Ubuntu 7.04.  The CPU scaling works fine, but I'm wondering about the temperature control.  Is there any way to link the CPU temperature to the scaling?  So if the processor is overheating (and crosses one of the pre-set temperature thresholds), it would try to scale back the processor speed before shutting my machine down?  It seems that it would be better to have a slower computer, than one that likes to turn itself off in the middle of doing something.  I know my laptop has sub-par cooling system, but it can run for days at the lowest setting and be fine.  And it can run at the highest setting for about 30 minutes before it gets too hot.  I have even had it turn itself off for overheating, let it sit for about five minutes, and in the process of turning it back on, it will overheat again - before the GUI even comes up.

---

### Post by gerbalblaste on 2007-08-11
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336](https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There is a bug report on launchpad having to do with this problem:
[https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336](https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336)

Try you luck with the solutions given there. It seems odd that this problem has persisted for two years without resolution.

---

