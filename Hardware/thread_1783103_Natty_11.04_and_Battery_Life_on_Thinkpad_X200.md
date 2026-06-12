---
title: "Natty 11.04 and Battery Life on Thinkpad X200"
date: 2011-06-15
forum: Hardware
---

### Post by MSwal2846 on 2011-06-15
Prior to installing Natty on my Lenovo Thinkpad X200 I was getting between 5 and 6 hours of run time with my battery.  I have fairly religiously worked at letting the battery drain as completely as possible prior to plugging in to keep the battery life optimized.

Then I installed Natty.

I've read through several threads concerning the Kernel issue that come with Natty and the impact that is having with battery life.  I'm down to just a couple of hours and it seemed to just keep dropping.  So over this past weekend I backed up everything and upgrade my kernel to "2.6.39-0-generic-pae" as the various forums seemed to indicate that would help.

It's now Wednesday and I'm getting about 2.5 - 3 hours of battery life ... which is about half of what I was seeing prior to Natty.  I've also installed the "thinkfan" in the hopes that would help.

Ok, so my questions:

[LIST=1]
[*]Why am I not seeing my original battery life?
[*]Is it because the issue in the kernel is not completely fixed by 2.6.39
[*]Or did Natty completely hose my battery?
[/LIST]

Thanks!

---

### Post by MSwal2846 on 2011-06-16
bump

---

### Post by Yellow Pasque on 2011-06-16
You might want to monitor the CPU usage and wakeups using htop and powerdevil.

---

### Post by MSwal2846 on 2011-07-26
So I've done the following that has helped significantly:

[LIST=1]
[*]Upgraded to Kernel Linux 2.6.39-3-generic-pae
[*]Installed "laptop-mode-tools" from Synaptic Package Manager
[*]Installed "powertop" from Synaptic Package Manager
[/LIST]

I'm not sure which of the three helped the most, but combined I'm back to getting about 5+ hours out of battery ... and it was relatively easy to do.

---

### Post by navr91 on 2011-07-26
MSwal, I'm looking to improve the battery life on my X220 in Natty. How did you upgrade the kernel?

Thanks!

---

### Post by ZaHACKieL on 2011-07-26
Well, as for my own experience, Natty is a little hotter and power consumer than other versions but I can't exactly say that it will half your battery life. Just one thing, for a Li-Ion battery it's not a good idea to drain it a recharge it to often. You should use it to ~30% of its capacity and then recharge it. How old is your laptop?

---

### Post by MSwal2846 on 2011-07-26
Use this:

           sudo add-apt-repository ppa:xorg-edgers/ppa 
           sudo apt-get update
           sudo apt-get install <package name>

Be sure to pick the proper linux package to install.  If not sure, I'd use the Synaptic Package Manager to pick the like version.

Good luck, I hope it helps!

---

### Post by navr91 on 2011-07-26
Looks like I was able to upgrade my kernel, because terminal had this to say about it:
```

uname -a
Linux reedemon 2.6.39-02063903-generic #201107091121 SMP Sat Jul 9 11:25:36 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

Thanks, MSwal! I'll install laptop-mode-tools, too, and see how it goes.

Also, how did you use laptop-mode-tools and powertop to increase your battery life? Did you have to configure them somehow? or enable them?

---

### Post by MSwal2846 on 2011-07-26
None.  To tell you the truth, I installed them with the intent of getting into them to experiment, but just have not had any time.  So they are exactly as they installed and I'm seeing great battery life.

---

