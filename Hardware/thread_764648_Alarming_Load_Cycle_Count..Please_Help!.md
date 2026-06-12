---
title: "Alarming Load_Cycle_Count..Please Help!"
date: 2008-04-24
forum: Hardware
---

### Post by yssida on 2008-04-24
First off, I'm a newbie, I have installed and dual-booted Ubuntu Gutsy and Ubuntu Hardy Beta, the former I'm using right now as my main OS. I have heard about this problem of extremely high load cycles in hard drives, as a recurring bug in Ubuntu, and I think very serious. I figured out how to check my Load_Cycle_Count by using smartctl.

This is the result.

```
choking@Minerva:~$ sudo smartctl --all /dev/sda |grep 193
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       10362

```

It seems to be very high, for a laptop hard drive (the whole thing was bought a month ago). I think a solution would be to switch over to Debian, but then I'm a little scared of hardware support and stuff. So I stay in Ubuntu. I tried various online suggestions (googled) which set the hdparm -B 255 , and then 128 and then finally to 254. Nothing happened, if anything it gets worse. As of writing the Load_Cycle_Count has gone up to 10390.

So I turn to the community for help. What other information do you need? I will gladly cooperate and post the required information, but please tell me how to get it. Please help me find a fix for this, I am a student and cannot afford to pay for a new hard drive.

Thank you.

yssida

---

### Post by yssida on 2008-04-24
bump

---

### Post by jespdj on 2008-04-24
See the big Load_Cycle_Count issue thread here:
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by yssida on 2008-04-24
I have already read the posts. and tried the hdparm, but didn'twork :(

---

