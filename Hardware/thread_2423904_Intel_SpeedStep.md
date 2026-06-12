---
title: "Intel SpeedStep"
date: 2019-07-31
forum: Hardware
---

### Post by tylerknut on 2019-07-31
I have an old laptop, Inspiron 1525, CPU is T4200 and it is running 18.04 LTS Server.
The laptop runs hot all the time, even though it is mostly idle.
I see CPU speed minimum is 1200, and I want it to go low as possible when idle, and ramp up as needed when the server is being used.  I'm unable to find documentation for T4200 which specifies how low it can go.
Is there a package that can do this automatically?  If I search for this type of functionality I find almost unlimited options but most threads end up saying it doesn't work, or they are focused on performance mode and opposite of what i'm trying to do.

---

### Post by aromo2 on 2019-07-31
You need to set the [cpu scaling governor]("https://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt") to conservative.

You can read how to do it [here]("https://askubuntu.com/questions/149271/how-to-change-default-scaling-governor-back-to-ondemand#149275")

---

### Post by CatKiller on 2019-07-31
> **tylerknut said:**
> I have an old laptop, Inspiron 1525, CPU is T4200 and it is running 18.04 LTS Server.
The laptop runs hot all the time, even though it is mostly idle.
I see CPU speed minimum is 1200, and I want it to go low as possible when idle, and ramp up as needed when the server is being used.  I'm unable to find documentation for T4200 which specifies how low it can go.
Is there a package that can do this automatically?  If I search for this type of functionality I find almost unlimited options but most threads end up saying it doesn't work, or they are focused on performance mode and opposite of what i'm trying to do.
That *is* as low as it can go: it has a bus speed of 200 MHz and a multiplier of between 6 and 10, meaning it can vary only between 1.2 and 2.0 GHz.

You can help it be in the lower states more often by use of different governors, and by using powertop to see what's pushing it into the higher states, but it can't go lower than its minimum without underclocking and undervolting which your BIOS and processor may not support.

If your concern is simply that your old laptop is running hot, that's a job for a can of compressed air.

---

### Post by tylerknut on 2019-07-31
> **CatKiller said:**
> That *is* as low as it can go: it has a bus speed of 200 MHz and a multiplier of between 6 and 10, meaning it can vary only between 1.2 and 2.0 GHz.


If that's the case, it's already doing what I want.  The CPU is only at 47C but the whole laptop is very warm all the time (sitting in 65 degree basement).  Maybe it's the hard drive and not the CPU...!

---

### Post by #&amp;thj^% on 2019-07-31
That's very possible, I had a WD Black 1TB Performance Desktop Hard Disk Drive, on my server that ran very warm all the time.
Bought a docking deck to rid my tower of the heat from the hard drive.
Also did you by-pass CatKillers advice on blowing out the machine, those dust-bunnies make a great thermal blanket.
Or Add more fans. ;)

---

### Post by tylerknut on 2019-07-31
Yeah it's the hard drive..  didn't realize where it was located.  I used a laser thermometer and the palm/touch pad is 105 in that area.  It is a 7200RPM hybrid laptop drive.  I do have the laptop elevated slightly for airflow, but this is the problem..  not the CPU or SpeedStep.  I'll try to get it to spin down when idle, that should help.

---

