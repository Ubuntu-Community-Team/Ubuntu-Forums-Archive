---
title: "[SOLVED] Power managment doesn't work"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by r!ots on 2008-01-13
Hey guys,
today I noticed a strange thing: my power managment settings aren't used or to be more exactly, not all of them.

On Battery Power it doesn't do what it's told in 'Put computer to sleep when inactive for: ...' and 'When battey power is critically low: ...'.
The putting to sleep doesn't really hurt me, since my laptop won't wake up after suspending and therefore I'm not even using it, but today it didn't shut down on low battery power, which before has always worked. There was even a pop-up which told me that the laptop would should down soon.
Why doesn't it shut down anymore? I haven't changed any power managment setting and as I already wrote, it always worked for me before.

edit:
I just tried it and the suspend and hibernate function do work. But still the problem stays the same: Why doesn't it suspend after the given idle time and why doesn't it shut down on low battery?

---

### Post by r!ots on 2008-01-14
OK, I got it working once again.
I added *acpi-cpufreq* to /etc/modules to give my laptop cpu frequency scaling support and that got suspend and hibernate working as well.
For the problem with the shut down on low battery I used the Configuration Editor to make it use the charge percentage of the battery instead of the calculated remaining time to determine when to shut down. Now it's working perfect again.

---

### Post by twrock on 2008-01-19
Thanks for posting what you did to get things working. For complete noobs like me, could you give a little more detail about steps for how you did all that? I'd really like to get those exact same problems resolved on my laptop, but I'm having a hard time figuring out how exactly to do it.

---

### Post by firefeather on 2008-01-19
> **r!ots said:**
> 
Why doesn't it shut down anymore? I haven't changed any power managment setting and as I already wrote, it always worked for me before.

I'm surprised you got it working. A lot of users have had a problem with getting power management working as shown in [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/121653").

---

### Post by twrock on 2008-01-19
I too have tried to follow a few threads around here that are dealing with these very frustrating power management issues. I've tried the ones I could figure out, but nothing has worked so far. So I wanted to try this possible solution too.

Like I said, I'm still a noob, but here's what I came up with over the last 30 minutes based on what r!ots posted.

Opened terminal and typed:
```
sudo gedit /etc/modules
```
Added the following to the end of that file:
> acpi-cpufreq
Saved and closed gedit.

Opened configuration editor.
Unchecked the following key:
/apps/gnome-power-manager/general/user_time_for_policy

Rebooted.

But it's way to late on my side of the globe to stay up and see if things worked. But I'll try to report back when I get some idea of what that did.

---

### Post by twrock on 2008-01-20
Since this thread is marked "Solved", I jumped over to another, similar thread to continue it: [http://ubuntuforums.org/showthread.php?t=653063](http://ubuntuforums.org/showthread.php?t=653063)

---

