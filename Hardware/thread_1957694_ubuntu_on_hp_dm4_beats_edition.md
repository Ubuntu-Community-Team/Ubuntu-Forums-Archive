---
title: "ubuntu on hp dm4 beats edition"
date: 2012-04-13
forum: Hardware
---

### Post by bobthe on 2012-04-13
I recently installed ubuntu on my machine. and its been heating up a lot. Is it because of the amd dual graphics my machine has? I dont know but it never does this with windows ever. can someone please help?

---

### Post by bobthe on 2012-04-13
someone please help!

---

### Post by 23senick on 2012-04-14
Hmm, wondering if I have the same issue (HP dm1)...anyone?

---

### Post by 23senick on 2012-04-14
I'm trying the Jupiter applet

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html) 

we'll see if it works...

---

### Post by 23senick on 2012-04-14
Not sure there was a noticeable improvement with Jupiter, so I tried the following tip from the same page as previous post:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

This does mean tweaking Grub (system file) so be warned it could cause boot problems, and take precautions eg save original grub file somewhere else first.  

I *think* there was a slight improvement - I was monitoring using Psensor and seemed to run 3 or 4 degrees cooler, but it all seems to depend how many tasks you're running.  I rarely run windows so it may be I never do enough to make it warm up. However I also trawled the net and found reviews mentioning that my machine tends to get hot - presumably the tester was using Windows so guess my dm1 suffers from heat due its hardware (it was reasonably priced!).

---

### Post by 23senick on 2012-04-21
A few more reflections on this issue. After the tweaks in previous posts temperature hovered around 60 degrees rather than 65 degrees.  But windows sits at around 52 degrees when idling, so I was in search of further improvements.

After doing some research I tried using the ATI/AMD proprietary graphics driver (go through system settings and additional drivers). There are two on my machine, the first did not work properly (screen constantly showed* incompatible hardware*) and so I tried the post-release version. After install got a message that it did not install properly and that it was not activated - though in fact it was.  

Results? the laptop did run at lower temperatures (around 57 degrees). Battery life seemed improved.  On the downside there were one or two graphics that displayed differently - eg when two windows were open only the first one had coloured close/minimise/maximise icons, even when you were working on the other one.  Also the ubuntu screen on boot looked slightly different.  Didn't leave this working for long so not sure if there are other downsides.

More info on switching between drivers in this thread

[http://ubuntuforums.org/showthread.php?p=11861312#post11861312](http://ubuntuforums.org/showthread.php?p=11861312#post11861312) 

I've also read that the new kernel in 12.04 will improve running temperature so may wait a few days for that.

---

### Post by bobthe on 2012-04-26
Ya I had the same problems as you. It would always mess up when installing the ATI/AMD drivers. Do you think its possible im getting these problems maybe because I'm on wubi?

---

### Post by 23senick on 2012-04-28
I'm not on Wuibi - which suggests that isn't the cause. But I'm no expert...

---

### Post by 23senick on 2012-05-12
Have been on 12.04 for a week...still runs hotter than windows (61-62 degrees) so am trying the AMD/ATI post release proprietary driver again.  Now hovers around 58 degrees.

---

