---
title: "Ubuntu 9.10, ThinkPad T43 CPU scalling problems"
date: 2010-01-25
forum: Hardware
---

### Post by sotirovlyu on 2010-01-25
Hello Ubuntuforums members,

I'm running Ubuntu 9.10 on a ThinkPad T43 with following specs:

**Model/type**: 2668-CTO/VYU
**CPU**: Intel Pentium M (Dothan) 2.0 GHz
**Chipset**: Intel 915PM
**I/O Hub**: Intel 82801FBM ICH6-M southbridge
**Video**: ATI Mobility Radeon X300

My problems are with cpu-scalling and my machine is staying almost all of the time at the lowest CPU speed - 800MHz. I cannot force it to change to 2.0Ghz or any of the other available fequencies above the minimum, neither with the gnome applet, nor with tools like cpufrequtils. Changing of governor, or trying to set the speed to fixed one are unsuccessful. 

As a result my system is very slow, and I can see from the gnome applet that from time to time it goes to 2GHz, but I'm not sure if this is not fake, because whenever I need the speed.. some CPU intensive task nothing happens (e.g. flash vidoes are tearing). 

This is the state as per cpufreq-info after boot:

> cpufreq-info
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.00 GHz:0.00%, 1.60 GHz:0.00%, 1.33 GHz:0.00%, 1.07 GHz:0.00%, 800 MHz:0.00%  (4446)
I have same problem if try Kubuntu 9.10 of course. Both with default kernel 2.6.31-14 and the latest from standard repositories - 2.6.31-17

I made a test with a earlier Ubuntu 8.04 LTS with kernel 2.6.24-26 and there the problem **does not **exist. CPU scaling is working correctly I can play the flash videos (easiest test that I can make) and all is fine - the system is obviously faster.

I read somewhere that after Ubuntu 9.04 acpi_cpufreq is already compiled into the kernel, and may be this is connected to my problem.

Could you please advice with some ideas if it is a known issue/bug, how to solve, etc. I'm found similar problems in launchpad, but not the same exactly, and no working solution for me.

**UPDATE:** After posting, I found and installed an unofficial 2.6.31-17 kernel with some modifications, most notably with acpi_cpufreq compiled as a module. [COLOR=Black]And currently CPU scaling works normally[/COLOR]. 

The kernel i installed is from "https://launchpad.net/~linux-phc/+archive/ppa" (linux-phc.org), which is meant for undervolting the CPU and replacing acpi_cpufreq with a module provided by linux-phc team. But by default after installing the modified kernel it boots with original acpi_cpufreq as module and I'm on this step, before preparing the phc module.

---

### Post by sotirovlyu on 2010-01-26
*bump*

Well, for me this issue is obviously a bug and I have to probably file it in bugs.launchpad (never did till now and I'm going to test it), but this was also my first post at Ubuntuforums, and when I see that tens of new topics are posted **every hour** only in this area of the forum.. I wonder who'll ever have the time, unless some big luck, to put an opinion on my topic. What about all other topics here...

Could somebody please explain me, how things in this forum work ? To me it looks that there should be some person(s) from Canonical on full time job only checking this area of the forum :-))).

Regards

---

### Post by JesVestervang on 2010-03-07
Well, I'm also pretty new in this forum but I have the same problem on my 1.86 GHz T43. Thanks for the tip on linux-phc.org! :-)

---

### Post by sotirovlyu on 2010-03-08
Hi there. 

linux-phc is useful for T43 anyway.. due to the heat problems of these series, though i haven't spent time till now to play with the voltages. More or less priority is to be able to use full cpu speed capacity. But I don't spend time on this neither :-). I have suspended any research on this.. may be planning to try to recompile ubuntu kernel on my own.. or try other distros.. because currently I'm not 100% sure if it is related to Ubuntu only or to vanilla kernel also.

I also posted a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/519142](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/519142)

But it never changed status from "New/Undecided/Unassigned" like I never posted it there.. I'm a bit disappointed from ubuntu "community" :-), the forum here and bug reporting. May be if you have the same issues like me, you can put your comment there also and some developers might take a look on it, i dunno how it works.

Or if you'll find some updates on this issue, you can post here.

Cheers

---

### Post by kleskjr on 2010-03-08
Hi guys,
I just run the cpufreq-info and got result 1000MHz, although my processor is 1830MHz.

So I loaded my system with a long and tedious script and checked again (many times) and then the cpu freq started to change (1, 1.33 or 1.83GHz) so try first to load your system and then check the frequancy 

cheers

---

### Post by sotirovlyu on 2010-03-11
hi kleskjr,

I'm not so sure I've understood what you did and what you mean by "loading" a system. You mean starting CPU intensive task ? For me is easy to check with some HD flash video.

---

### Post by kleskjr on 2010-03-11
Hi,

I just tried again and realized that the result coming from 'cpufreq-info' is a bit buggy. It updates just sometimes the printed values in the terminal (on the last line the number in the brackets is some cpu time, if it does not change it means that it does not update the printed text). I hope that the problem is not in your cpu but rather in the cpufreq program.

You can try another test(in Ubuntu): right click on your top panel and select add to panel, then choose CPU Frequency Scaling Monitor, hope that this will work fine for you. With this program actually you can also control the cpu speed.

---

