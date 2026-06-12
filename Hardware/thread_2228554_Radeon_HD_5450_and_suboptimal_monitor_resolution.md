---
title: "Radeon HD 5450 and suboptimal monitor resolution"
date: 2014-06-08
forum: Hardware
---

### Post by saeed5 on 2014-06-08
Hi

I just wanted to know if I can expect to install my Radeon HD 5450 on Linux 14? Are 5000 series supported in the latest Linux version?

If so, please let me know how I can install the appropriate drivers. I'm a novice, so please be kind.

Many Thanks

---

### Post by coffeecat on 2014-06-08
By "Linux 14" I assume you are referring to the latest Ubuntu release, 14.04. If you are, the Radeon 5450 should work just fine with the default radeon open source driver. You won't have to install anything. It probably won't be suitable for video-intensive games, but if you are a serious gamer I doubt you'd be using that card anyway.

---

### Post by saeed5 on 2014-06-08
Hi coffeecat

Yes, I meant the latest version. I have already installed it and the resolution is below my Monitor's standard. How can I increase it? It show be 85 hz but it is 60 by default. 

Issuing Xrandr -q, reveals

1024*768       60.0*
800*600         60.3
848*480         60.0
640*480         59.9

By the way, installing the ATI binary X.Org driver from Ubuntu Software Center was tragic. The monitor gave "Out of frequency" alert. I had to reinstall the OS.

Any ideas?

Thanks

---

### Post by coffeecat on 2014-06-08
I've edited your thread title in order to attract those who can help. From what you say, this sounds to be more of a monitor problem - perhaps it is not putting out accurate EDID, if at all. I suggest you post details of the monitor. 85Hz sounds like an old CRT monitor. Is it CRT?

> **saeed5 said:**
> I had to reinstall the OS.

Actually no. :) A couple of commands in a recovery console (which is text-only and doesn't use the proprietary video driver) would have uninstalled the proprietary driver. For future reference, if you think you need to re-install the whole OS, start a thread first asking for opinions. You may be pleasantly surprised!

---

### Post by saeed5 on 2014-06-08
Hi again

Yes it is an old, faithful CRT monitor. 
But, I think I found the answer to my trouble [here]("http://askubuntu.com/questions/189246/how-set-my-monitor-resolution"). I now have the higher resolution. :P

Thanks.

---

### Post by saeed5 on 2014-06-08
The only problem, now, is when I restart the resolution reverts back to 60. Any ideas how I can fix it at 85 for good?

---

