---
title: "Hibernation Problem"
date: 2011-08-22
forum: Hardware
---

### Post by Gwaro on 2011-08-22
I am running Ubuntu 11.04 on my Dell Vostro 1015 machine.When i set it to Suspend or Hibernate mode,the screen goes off(as expected) but the Num Lock and Caps Lock indicators start blinking on and off  and i cant get the machine back running  unless i manually shut it down by the Power button and then cold boot it.
Is this ok?What could be the problem?

---

### Post by VogonZarniwoop on 2011-08-22
I know this isn't much help to you, but what you describe is also my experience trying to get hibernate to work under Linux on many different systems from laptops to desktops.  I have only seen ONE system where I could get it working, that was an eeepc netbook.  On everything else, I see exactly what you describe: it will enter hibernation but won't come back out and needs a hard reboot.  I see the same with suspend.  Unfortunately, most Linux projects seem to find it much more exciting to add new features rather than to fix existing problems, so I don't have much hope this will ever be addressed.  You can find literally _hundreds_ of threads around the internet of people complaining about broken hibernation, and dozens of different workarounds that work for some people, but not others.  But the answer is usually, "just get the source and fix it yourself if you have a problem". That's really an irritating thing to read, because (a) most people can't, (b) even if they can, it takes a huge amount of time to figure out how the existing code works if you didn't write it, and (c) this attitude is a big chunk of why Linux has failed to get more than 1% share of the desktop.  Problems impacting many people go unfixed for many years.  I routinely encounter various problems and when I google them, I find people complaining of the very same thing 6 or 8 years ago.  Sometimes there are workarounds, sometimes not.  Sometimes there are like 10 proposed workarounds and it takes hours to try them all and see if any are going to work.

 I wish I could help you better, but all I can do is empathize and say I've seen exactly the same thing on 7 of 8 systems across 3 Linux distros and 15+ different versions including old ones and bleeding edge.  I've given up on suspend/hibernate features, and just decided that the price I have to pay to use open source software is that a ton of basic stuff doesn't work right. It's still worth it overall I think.

---

### Post by aloksethi on 2011-08-22
num lock n caps lock blinking means kernel has panicked
by any chance have u installed virtual box 4.1?
i had the same issue with virtual box 4.1, reverting it back to 4.0 fixed my problem

---

### Post by VogonZarniwoop on 2011-08-22
I don't know about the OP, but most of the machines I've seen this on don't have VirtualBox installed.

---

### Post by Gwaro on 2011-08-24
> **aloksethi said:**
> num lock n caps lock blinking means kernel has panicked
by any chance have u installed virtual box 4.1?
i had the same issue with virtual box 4.1, reverting it back to 4.0 fixed my problem

Yeah i have got it installed and i am going  to try what you,ve said.

---

### Post by Gwaro on 2011-08-24
It worked !

---

