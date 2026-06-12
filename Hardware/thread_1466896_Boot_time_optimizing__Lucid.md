---
title: "Boot time optimizing / Lucid"
date: 2010-04-30
forum: Hardware
---

### Post by mexp on 2010-04-30
So I read about boot time improvements on Lucid Lynx, and got disappointed to see some 40+ sec boot time on my laptop. Resuming from standby is far better. I think this laptop, Latitude D620, a couple years old, should do better.

What there is to do to improve? I did an upgrade instead of a fresh install, does that make a difference? 

Here's the bootchart: [http://www4.picturepush.com/photo/a/3354697/img/3354697.png](http://www4.picturepush.com/photo/a/3354697/img/3354697.png)

---

### Post by cespinal on 2010-04-30
+1 here running kubuntu. It did get slower..

---

### Post by leithon on 2010-05-01
i have the same problem, in fact without splash... I'm trying to solve the splash problem, is it related?

---

### Post by acfreema on 2010-05-01
When I tried the beta a few weeks ago, I saw that grub2 was used, and became quite disappointed.  The second thing that I did after installing 9.1 was change to lilo; no more sitting for 13 seconds at the OS selection menu.

Changing to grub legacy is hard enough to make it completely undesirable, so lilo is the obvious solution.  A quick uninstall, a quick install, short man-page reading , and a brief configuration results in much faster booting.  Lilo has my vote until grub2 either gets ditched or improved.

By the way, Ubuntu is the only distribution I've used that implements grub2.

---

### Post by IcarusR on 2010-05-01
acfreema  > 13 seconds at the OS selection menu.

Timeout on the main (OS selection) Grub2 screen can be altered quite easily.

A good guide to Grub2 [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")


> Boot time optimizing / Lucid

Some suggestions here [http://wiki.debian.org/BootProcessSpeedup]("http://wiki.debian.org/BootProcessSpeedup")

Ubuntu Tweak may help [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

Boot-Up Manager gui to turn off unwanted services [http://www.marzocca.net/linux/bum.html]("http://www.marzocca.net/linux/bum.html")

Compiling your own kernel without not needed modules can speed bootup considerably.

---

### Post by acfreema on 2010-05-01
I did my due diligence and searched many forums and blog posts related to this topic with no success; I changed the settings to be the fastest possible with no changes.  The easiest solution is using lilo.

---

### Post by mexp on 2010-05-02
So I guess starting up the services takes a long time, and there certainly are some that are not being used. But is there a guide to Ubuntu services? I only found a comprehensive one from year 2005 on this forum.

Still repeating the first question, does it make a difference in start-up time if I did a fresh install instead?

---

### Post by mexp on 2010-05-02
And about readahead - there's installed ureadahead and sreadahead, so probably that means that it is already used in the system? 

I changed the shell in to dash, and that perhaps shaved the startup time by 2-3 seconds. Still not very impressed...

---

### Post by AbtZ on 2011-05-05
> **mexp said:**
> Still repeating the first question, does it make a difference in start-up time if I did a fresh install instead?

Can't believe nobody answered this question... The thread is old now, but for completeness sake: YES a fresh install is a lot better than an upgrade if you wish to have a faster boot.

---

