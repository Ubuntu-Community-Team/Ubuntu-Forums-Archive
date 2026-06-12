---
title: "ubuntu crash with no reason !!"
date: 2008-11-11
forum: General Help
---

### Post by Martiini on 2008-11-11
ubuntu crahed on my hp dv6565en laptop .. with no apparent reason.
i suspect it was kernel fault because all hardware seems ok .. and ive had no problems before.
i suspect kernel fault because when it crashed .. caps lock light stayed on blinking

---

### Post by Kevbert on 2008-11-11
May be worth running memtest from the boot menu.

---

### Post by xueg0i on 2008-11-11
I also have random crashes on my HP dv6000 laptop since 8.10. It is a Turion dual core AMD64 with a NVidia gpu. I already checked my mem, but no errors. Also no clues in the logs as far as I can see. Are there more people out there with the same problem on their (HP) laptop?

---

### Post by billgoldberg on 2008-11-11
> **xueg0i said:**
> I also have random crashes on my HP dv6000 laptop since 8.10. It is a Turion dual core AMD64 with a NVidia gpu. I already checked my mem, but no errors. Also no clues in the logs as far as I can see. Are there more people out there with the same problem on their (HP) laptop?

My hp pavilion dv4000 is pretty much useless after two years.

I bought it for &#8364;1400 two years ago and now I use it for nothing more than a paper weight.

It's been in repair shops and with hp for more time than I used it.

Three months after getting the motherboard, cpu, hdd, memory, ... replaced (for free) by hp, it's unusable again.

It won't start with the battery in it, after using it for around 15 minutes (doesn't matter which OS), it shuts down.

I'm never buying HP laptops again.

---

### Post by brennsuppa on 2008-11-14
same story here!
since the update the system randomly but i have no hp. i work on a dell inspiron 6000

some times it's working for hours and then its crashing all the time but i cannot find a reason!

first i thought it's something in the aliases, because there was an error about a bad line, but the system is still crashing!

---

### Post by Mr. Picklesworth on 2008-11-14
Quick research tells me that your computer has Intel Wireless WiFi Link 4965 AGN. (Same as mine). Brennsuppa, could you check that as well, please? If you don't know for sure, just right click on the network management thing in your Notification Area and choose Connection Information. If the driver is iwlagn, you probably have the same problem.

Sounds like the infamous [Intel WiFi kernel panic]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/286285").

It's a really unfortunate bug. Should have been treated as a show-stopper since it affects a huge number of users and has lasting repercussions that must be dealt with manually. In fact, I think this is the source of almost every problem people are having with Intrepid since the thing is *solid* once the bug is fixed.

Anyway, there is a possible fix in the Proposed Updates repository. If you feel like it, go to System -> Administration -> Software Sources, then click the Updates tab. Check "Pre-released updates (intrepid-proposed)". Keep in mind that these are proposed for a reason; they aren't fully tested!
After closing that dialog it will offer to refresh your repository list. It will detect available updates, some of which should be for the kernel. That update *will* take a while.
Upon restarting, the problem should be solved. If hibernate / suspend didn't work for you before, you may be pleasantly surprised. Whatever happens, it would be *much appreciated* if you post the outcome on that bug report, whether it works for you or not. I would love to see this move to the stable release really soon. (And maybe the images rebuilt since it is an absolute disaster of a bug).

You may want to purge your system logs, as well. Check if /var/log is really huge; this bug is known to spew log messages like crazy. Easy way to do that is to open System -> Administration -> System Log, check the various logs available on the left while reading the log size mentioned at the bottom. (And if the thing freezes, you'll know that the log is indeed consuming a lot of space). That's the reason I suspect this bug is responsible for a lot more than just kernel panics; having the system log consume all of / means that admin tools can't create locks and everything moves like mollasses. For a while, Intrepid felt like Windows to me.
The proposed fix resolved the problem for me, by the way ;)

---

### Post by bapoumba on 2008-11-14
Moved to General Help.

---

### Post by richardspirit on 2008-11-18
My computer also randomly crashes for no reason but I am running a custom box. I am running an AMD Sempron with a Gigabyte motherboard. The hardware is about 3 years old but the hard drive maybe much older. 

It could very possibly be a hardware problem but I want to exhaust all other possibilities first. 

My Amarok also crashes everytime I try to open it but it was working fine yesterday. 

And my sound will randomly disappear and then come back after a few seconds.

---

### Post by gjoellee on 2008-11-18
> **billgoldberg said:**
> My hp pavilion dv4000 is pretty much useless after two years.

I bought it for €1400 two years ago and now I use it for nothing more than a paper weight.

It's been in repair shops and with hp for more time than I used it.

Three months after getting the motherboard, cpu, hdd, memory, ... replaced (for free) by hp, it's unusable again.

It won't start with the battery in it, after using it for around 15 minutes (doesn't matter which OS), it shuts down.

I'm never buying HP laptops again.

HP laptops have never been good in my oponion however HP desktop PC's are fine. DELL is the best when it comes to support and stuff...!

---

### Post by Mr. Picklesworth on 2008-11-18
Folks, please, this isn't a thread to bash HP. This is most likely an issue prompted by some kind of kernel-level incompatibility and is occurring only after an upgrade. While it isn't improbable for a software upgrade to expose, for example, an overheating problem, it is not the definite answer and certainly not what we should assume. For the record, I have a hunch that the issue lies squarely with Intel of all companies. (And I for one quite respect Intel, so am *gasp* not holding a grudge or expecting them to explain themselves; just to fix it and learn from it).

It is very unlikely that the software upgrade has anything to do with the computer's build quality, and I am sure Martiini would appreciate if you guys did not attack his choice of product. It generally doesn't make people feel very happy when they are told that something they own is bad.

Martiini, have you tried the kernel in the proposed updates repository? I would be *really* interested to know if it works. I do recommend backing up your stuff ahead of time if you haven't already, but what's the worst that could happen? :)

---

### Post by smallroad on 2008-12-22
Just thought I'd pass on my experience here as it may help someone else...

I instlled Ubuntu 8.10 a few weeks ago and found that it would crash several times a day, I found this thread and checked for the iwlagn driver but was using ipw2200 so that blew that idea! I did however enable "Pre-released updates (intrepid-proposed)" as suggested by Mr. Picklesworth and came across the proprietary driver 'ATI/AMD proprietary FGLRX graphics driver', I installed and activated this driver and have had no crashes for almost a week. :P

I am using a 3year old Toshiba Satellite M40.

Hope this helps....

Smallroad.

---

### Post by richardspirit on 2008-12-23
> **smallroad said:**
> Just thought I'd pass on my experience here as it may help someone else...

I instlled Ubuntu 8.10 a few weeks ago and found that it would crash several times a day, I found this thread and checked for the iwlagn driver but was using ipw2200 so that blew that idea! I did however enable "Pre-released updates (intrepid-proposed)" as suggested by Mr. Picklesworth and came across the proprietary driver 'ATI/AMD proprietary FGLRX graphics driver', I installed and activated this driver and have had no crashes for almost a week. :P

I am using a 3year old Toshiba Satellite M40.

Hope this helps....

Smallroad.

I have been using that driver since 8.04 so I don't think that is my issue but thanks anyway.

---

