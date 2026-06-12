---
title: "Locking up after 5 minutes of battery usage (HP nc6400)"
date: 2012-02-28
forum: Hardware
---

### Post by cpmcdaniel on 2012-02-28
My HP nc6400 running Ubuntu 11.10 is locking up consistently after 5 minutes of battery-only power. It has been doing this for months now. My first assumption was that it was a bad battery, so I ordered a new one. It behaves exactly the same. Once the lock up occurs, I have to power it off hard, and then it locks up again immediately when Ubuntu loads. 

I need help identifying next steps and need tips to troubleshoot this further. I have tried tailing the kernel logs in a Terminal window as the lock-up happened. There is no warning in the log prior to lock up. Here are some things I intend to try next:

[LIST]
[*]SSH from another box and see if networking is still working after the lock up.
[*]Try running the BIOS utility after the lockup and see how long it lasts on battery power (to verify if it is a battery or hardware problem)
[/LIST]

If you can think of anything to add to this list, please help me out. I will post updates.

If anyone has seen this behavior before, please chime in.

---

### Post by cpmcdaniel on 2012-02-28
OK, I just booted up without power chord and I've been running 10 minutes with no crash. Power Statistics has the following to report about my battery:

Energy 41.5 Wh
Energy when full 47.5 Wh
Rate 18.9 W
Time to empty 2.2 hours
Percentage 87.4%

So far so good...wish I could figure out what triggers it. It seems to happen pretty consistently after 5 minutes when the battery is fully charged and the power cable is removed.

---

### Post by ZootHornRollo on 2012-03-03
Have had similar problems myself.  Now using OpenSuse 12.1.

[http://ubuntuforums.org/showthread.php?t=1882876](http://ubuntuforums.org/showthread.php?t=1882876)

---

