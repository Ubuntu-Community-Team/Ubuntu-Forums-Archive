---
title: "Dell Dimension 9200C: noisy under Ubuntu 14.04: high CPU load"
date: 2014-07-18
forum: Hardware
---

### Post by UBUminJ on 2014-07-18
I got an old Dell Dimension 9200C - 2008 model. Freed it from Windows and plan to use it as a learning tool (hardware, software).
As my main PC runs Ubuntu 14.04, I also installed it on the old Dell too.

Very noisy, either the fan or the harddisk (Samsung SP2504C). Most probably the fan, as the CPU load changes constantly from 5 to 99%.
How can I find in details what processes are responsible for this huge cpu load. I know about "top" and "lm-sensors".

Is there anything else which I can use to analyze hardware-based problems.

If nothing helps, I am going to reduce the OS load by installing Lubuntu e.g. - I already found with other old hardware that some WinXP models are not powerful enough for Ubuntu. Under Ubuntu, their fan was in "competition mode" - 100% on :-), under Lubuntu, they hardly move.

I already checked all available Dell Dimension 9200C information on ubuntuforums and other internet sites.

Thank you in advance.
Michael

---

### Post by slooksterpsv on 2014-07-19
You can also install and run powertop and it will help you get the system running a bit better by reducing fan noise issues. Hmm... Core 2 Duo, I'd try powertop, you may be able to tweak other settings. My fan kicks on quite a bit with Flash videos. What is the typical load for usage, apps wise?

---

### Post by UBUminJ on 2014-07-22
The fan had to work a lot, so I installed a lubuntu-based distro which is said to have a low footprint: lxle-1404-64
The difference is easy to hear but still the fan has to work a lot from time to time.
If I look at a youtube video with firefox, the plug container alone uses 20% of the CPU. And soon after, the fan starts roaring.

Could also be a hardware problem - near the power supply, it is really hot - very different from my main PC.
We'll see - a lot of stuff to learn.

Thanks for the info about powertop.

---

