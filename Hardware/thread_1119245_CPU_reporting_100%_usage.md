---
title: "CPU reporting 100% usage"
date: 2009-04-07
forum: Hardware
---

### Post by xanfantasy on 2009-04-07
After updating Jaunty beta with the daily updates, my cpu has started to report a constant 100% usage in the system monitor under Resources and the screenlets monitor. I checked all processes and they didn't add up to 100% at any time. After killing the extra processes, it still reported 100% usage. My processor is an AMD Athlon64 3700+. Any reason why it's doing this?

---

### Post by Dark_Stang on 2009-04-07
Is powernowd working correctly? Reinstall that to make sure it's working.

---

### Post by xanfantasy on 2009-04-07
I did a reinstall using terminal and after starting powernowd it replied with:
"CPU frequency scaling not supported...   "
Not sure if this would affect anything but the monitor has worked before 9.04 (I started with 7.10).

one other thing is, I think it may actually be inversing, thinking that 0% load is 100% load. It looked like if you added up the processes in system monitor and subtracted that from 100, it gives the processor load.

---

### Post by Dark_Stang on 2009-04-07
It sounds like your processor is running at 100% because Ubuntu 9.04 no longer supports scaling down on your CPU. This means that your processor is running at full throttle all the time. I'd try either reinstalling 9.04 from a clean install (and hope that it works) or go back to 8.04 or 8.10 (assuming those worked).

---

### Post by xanfantasy on 2009-04-09
do you know where the configuration file for powernowd is? could I delete the file then reinstall the program to reconfigure it?

---

### Post by xanfantasy on 2009-04-10
started doing some searches (should have done it before posting) but I found a ubuntu wiki [guide]("https://wiki.ubuntu.com/PowerPCKnownIssues") on Scaling issues, I will try their solutions to see if they work.

---

### Post by warpslide on 2009-04-10
I was having this same issue.  My CPU was running at 100%, and the fan was running very fast and loud on my laptop causing my battery to deplete very quickly.

After following xanfantasy's suggestion to follow this [link]("https://wiki.ubuntu.com/PowerPCKnownIssues"), I was able to resolve the issue.

"Option A" under "Processor Scaling" worked for me.

I use a Dell Inspiron 1525 with Ubuntu 9.04 Beta. (Upgraded from Ubuntu 8.10).

Thanks again!

---

### Post by xanfantasy on 2009-04-10
After my senior project, I reinstalled Jaunty and deleted the old configuration files. The system monitor shows the correct percentage under resources >> CPU History as well as the other monitors (gnome bar and screenlets) but the scaling is still unsupported. I tried both a and b but neither worked for me. A didn't seem to do anything, and I couldn't remove powernowd. 

I'm not too worried about the scaling though. My first computer randomly produced a post code "CPU Failure due to overclocking." bad thing is, I barely knew what overclocking was at the time. I'll stick to fans going full speed all the time.

Congrats on getting it working on your dell though, glad I could help.

---

