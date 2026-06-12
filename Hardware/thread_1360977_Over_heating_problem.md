---
title: "Over heating problem"
date: 2009-12-21
forum: Hardware
---

### Post by imacyh.com on 2009-12-21
Hi
I am having a serious problem with ubuntu 9.10, the system raise the computer tempreture to a not normal level and the system freeze after that. I lose all my an saved work.
The problem is repeating over and over in a way i can't use the system any more, last time the system freezed after 2 minutes from starting, if i restarted the computer right after it freezed i get this message "Critical temperature reached ... Shutting down"

I never had this problem before with the original os ( Vista ) or any previous version of ubuntu, anybody has an idea about a solution?
My computer is a laptop HP/Compac Presario A900

---

### Post by LinuxDeal on 2009-12-21
Welcome to the forum!

1. Open the system monitor (System > Admin > System Monitor) and find out which process is using the most CPU.  Under the processes tab click % CPU twice to sort by CPU usage.  Unfortunately system monitor is somewhat of a resource hog itself.

Hopefully this will tell you what part of your system is causing the problem.

2.  If that doesn't help, search google for "presario a900 ubuntu karmic"
Try adding other keywords if the results are nonspecific.

---

### Post by imacyh.com on 2009-12-21
Thanks for welcoming me and your reply
the system monitor showed that firefox and skype beside the system monitor itself are using the cpu, the numbers are not high now and the system seems to be stable now, the fan sound is not high and there is not very hot air is coming out.
I don't understand, i was having problems all the day with it and now seems to be working.
I started the update manager, usually it freeze when i do but it didn't although it used lots of the cpu and hot air was coming out and the fan sound got louder.
Dose the kernal has to do anything with this? My kernal is 2.6.31.16

---

### Post by MyR on 2009-12-21
Update manager is expected to use cpu and consequently make the processor hotter.  Freezing is not expected behavior and you will need to reproduce the problem with system monitor running to diagnose the cause.

You are running the latest kernel.

---

### Post by imacyh.com on 2009-12-21
I will keep an eye on the system monitor to see if i can put my hand on the problem. thanks everybody.

---

### Post by adam814 on 2009-12-21
Have you tried running sensors-detect from the lm-sensors package?  When I ran Jaunty I had an overheating problem until I ran it and found out the coretemp module needed to be loaded.

---

### Post by imacyh.com on 2009-12-22
> **adam814 said:**
> Have you tried running sensors-detect from the lm-sensors package?  When I ran Jaunty I had an overheating problem until I ran it and found out the coretemp module needed to be loaded.
I am sorry, don't understand, what do you mean by sensors-detect from the lm-sensors package?

---

### Post by adam814 on 2009-12-23
> **imacyh.com said:**
> I am sorry, don't understand, what do you mean by sensors-detect from the lm-sensors package?
Open a terminal and type this:
> sudo aptitude install lm-sensors
After that finishes type this:
> sudo sensors-detect
Follow the on-screen instructions.  I can't recall if it actually adds the modules for you or just tells you the names of the modules to add to /etc/modules, but either way it would let you know if you need one you're not using.

---

### Post by nishant.singh28 on 2009-12-23
Check your computer temperatures periodically to see if anything appears offhand.....I had a similar problem and it turned out that a Windows 7 crash  2 days ago had blown my heat sink. Had it replaced...so check out if all your temperatures are normal. Overheating could be due to failed hardware too.....timings can coincide.

---

### Post by cascade9 on 2009-12-23
Check that its not a hardware/cooling issue. Make sure the vents (bottom of the laptop and left hand side) arent clogged with dust, etc. 

If you want to know exactly where they are, check here-

[http://h10032.www1.hp.com/ctg/Manual/c01295803.pdf](http://h10032.www1.hp.com/ctg/Manual/c01295803.pdf)

BTW, blowing out the vents with a 'can of air' might be a good idea. You could even go as far as to remove all the hatches on the laptop and give everything a blow out as well...it cant hurt and should help if its a dust issue.

---

### Post by MyR on 2009-12-23
> **nishant.singh28 said:**
> Check your computer temperatures periodically to see if anything appears offhand.....I had a similar problem and it turned out that a Windows 7 crash  2 days ago had blown my heat sink. Had it replaced...so check out if all your temperatures are normal. Overheating could be due to failed hardware too.....timings can coincide.

A software crash can blow a heat sink?

---

### Post by cascade9 on 2009-12-24
> **MyR said:**
> A software crash can blow a heat sink?

Technically, maybe. Heatsinks dont 'blow', no matter what you do (the fan sure can though LOL). Fan failure could, however, be software related. That would be very, very rare though.   

But the other way around, heatsink fan failure, heatsink clogged with dust or thermal paste cooked is a cause of crashes.

---

### Post by nishant.singh28 on 2010-01-08
> **cascade9 said:**
> Technically, maybe. Heatsinks dont 'blow', no matter what you do (the fan sure can though LOL). Fan failure could, however, be software related. That would be very, very rare though.   

But the other way around, heatsink fan failure, heatsink clogged with dust or thermal paste cooked is a cause of crashes.
By blew, I meant it to be figurative, although it's not very rare in my case. Twice has Windows crashed on my 6 month old Laptop and both time, after a new install, I find out that my system is not cooling down and the heat sink is gone *poof*. Too much for a coincidence eh??

---

