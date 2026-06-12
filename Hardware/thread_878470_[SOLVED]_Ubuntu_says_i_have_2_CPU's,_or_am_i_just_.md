---
title: "[SOLVED] Ubuntu says i have 2 CPU's, or am i just mistaken?"
date: 2008-08-02
forum: Hardware
---

### Post by ilikeroflcopters on 2008-08-02
I dont know if my computer has 2 CPU's or not. When i look in the System Monitor at my CPU history it says CPU1 and CPU2 and both have different percentages of use.And my conky gadget on my desktop also says 2 CPU's with varying percentages.Im running a Sony Vaio PCG-GRT360ZG laptop with Ubuntu 8.04. It has a Mobile Intel Pentium 4 3.06Ghz processor.I attached a screenshot of the system monitor.Am i just being mistaken and it really has one CPU? I appreciate any help you can give me:)

---

### Post by articpenguin on 2008-08-02
Some pentium 4s have hyperthreading. I dont know much about HT but it has something to with multiprocessing on one core.

---

### Post by stchman on 2008-08-02
> **ilikeroflcopters said:**
> I dont know if my computer has 2 CPU's or not. When i look in the System Monitor at my CPU history it says CPU1 and CPU2 and both have different percentages of use.And my conky gadget on my desktop also says 2 CPU's with varying percentages.Im running a Sony Vaio PCG-GRT360ZG laptop with Ubuntu 8.04. It has a Mobile Intel Pentium 4 3.06Ghz processor.I attached a screenshot of the system monitor.Am i just being mistaken and it really has one CPU? I appreciate any help you can give me:)

That processor I believe has two logical processors somewhat like a dual core processor.

---

### Post by tamoneya on 2008-08-02
it has one CPU but it has something called hyper threading which makes it appear as two logical CPUs.  This helps it manage multi-tasking better.

[http://en.wikipedia.org/wiki/Hyper_threading](http://en.wikipedia.org/wiki/Hyper_threading)

---

### Post by noobuntu35 on 2008-08-02
wikipedia isn't a real good source of information but HT or Hyper Threading which the P4 supports would in fact make it appear as two logical CPUs. It was the an attempt to give the consumers "dual core operating" without the then "dual core price" alas it still only supports 32 bit processing

---

### Post by ilikeroflcopters on 2008-08-03
> **tamoneya said:**
> it has one CPU but it has something called hyper threading which makes it appear as two logical CPUs.  This helps it manage multi-tasking better.

[http://en.wikipedia.org/wiki/Hyper_threading](http://en.wikipedia.org/wiki/Hyper_threading)
thanks for the link. it cleared up the confusion i had.


> **noobuntu35 said:**
> wikipedia isn't a real good source of information but HT or Hyper Threading which the P4 supports would in fact make it appear as two logical CPUs. It was the an attempt to give the consumers "dual core operating" without the then "dual core price" alas it still only supports 32 bit processing

Does this mean it gives my CPU somehwat of a speed boost?Would this affect the CPU temperature?Because ive had trouble with my CPU overheating in the past with Windows XP, which is why i switched to Ubuntu

---

### Post by tamoneya on 2008-08-03
> **ilikeroflcopters said:**
> thanks for the link. it cleared up the confusion i had.




Does this mean it gives my CPU somehwat of a speed boost?Would this affect the CPU temperature?Because ive had trouble with my CPU overheating in the past with Windows XP, which is why i switched to Ubuntu

Glad to clear things up.  If you look at the article you will see that it gives about 15-30% speed boost.  This however doesnt come with a significant increase in temperature.  The cooling for your PC should have been designed to accommodate the processor that they installed.  Most likely you should try to clean dust out of your case or possibly replace some of your fans.

@noobuntu35: I think wiki is a perfectly good source in this case.  I realize how it is not an authoritative source but in this case it provides the basic understanding that the OP needed.  None of the statements that you made were contradicted in the wiki article.

---

### Post by ilikeroflcopters on 2008-08-03
> **tamoneya said:**
> Glad to clear things up.  If you look at the article you will see that it gives about 15-30% speed boost.  This however doesnt come with a significant increase in temperature.  The cooling for your PC should have been designed to accommodate the processor that they installed.  Most likely you should try to clean dust out of your case or possibly replace some of your fans.

Yea. I usually clean it from the outside and blow dust from the vents with compressed air. But this just cleans the vents. I havent been able to find any disassembly manuals for my laptop, and i dont know how to get to the actual CPU fans.

---

### Post by tamoneya on 2008-08-03
i forgot it was a laptop.  Most likely you shouldnt really mess with the fans and replacing them.  Take a look into intel speed step and cpufreq.  This will allow you to run the processor at a lower speed until you need more processing power at which point it increases the processor speed.  On my laptop I use it and most of the time it runs at 800 Mhz until it needs more at which point it goes to 2 GHz.  Not only does it reduce heat but it also increases battery life.

Note: Im not sure if that processor supports Intel speed step.  I dont remember when they introduced the feature.

---

### Post by ilikeroflcopters on 2008-08-03
> **tamoneya said:**
> i forgot it was a laptop.  Most likely you shouldnt really mess with the fans and replacing them.  Take a look into intel speed step and cpufreq.  This will allow you to run the processor at a lower speed until you need more processing power at which point it increases the processor speed.  On my laptop I use it and most of the time it runs at 800 Mhz until it needs more at which point it goes to 2 GHz.  Not only does it reduce heat but it also increases battery life.

Note: Im not sure if that processor supports Intel speed step.  I dont remember when they introduced the feature.

Can you possibly tell me where to find out how to do this?
Ive tried looking on Intel's website about Intel speed step

---

### Post by noobuntu35 on 2008-08-03
> **tamoneya said:**
> Glad to clear things up.  If you look at the article you will see that it gives about 15-30% speed boost.  This however doesnt come with a significant increase in temperature.  The cooling for your PC should have been designed to accommodate the processor that they installed.  Most likely you should try to clean dust out of your case or possibly replace some of your fans.

@noobuntu35: I think wiki is a perfectly good source in this case.  I realize how it is not an authoritative source but in this case it provides the basic understanding that the OP needed.  None of the statements that you made were contradicted in the wiki article.

You're right about the over heating in the cpu either a case change or too much dust in the case or fans.
I have a habit of pointing out that wiki's can be unfounded, however they usually say so, so yes in this case Kudos to the WIKI :)

---

### Post by noobuntu35 on 2008-08-03
> **tamoneya said:**
> i forgot it was a laptop.  Most likely you shouldnt really mess with the fans and replacing them.  Take a look into intel speed step and cpufreq.  This will allow you to run the processor at a lower speed until you need more processing power at which point it increases the processor speed.  On my laptop I use it and most of the time it runs at 800 Mhz until it needs more at which point it goes to 2 GHz.  Not only does it reduce heat but it also increases battery life.

Note: Im not sure if that processor supports Intel speed step.  I dont remember when they introduced the feature.

Hey lap tops are a Pain here's a cool (no pun intended) link to a DIY for cleaning a laptop from start to finish. [here]("http://www.fonerbooks.com/lap_fan.htm")

---

### Post by tamoneya on 2008-08-03
Here is a nice link about speed step: [http://www.bay-wolf.com/speedstep.htm](http://www.bay-wolf.com/speedstep.htm)
There is also the wiki article: [http://en.wikipedia.org/wiki/SpeedStep](http://en.wikipedia.org/wiki/SpeedStep).  

Start by looking in your bios.  You can also try installing cpufreq on ubuntu:```
sudo apt-get install cpufrequtils
sudo cpufreq-info
```

---

### Post by ilikeroflcopters on 2008-08-03
> **tamoneya said:**
> Here is a nice link about speed step: [http://www.bay-wolf.com/speedstep.htm](http://www.bay-wolf.com/speedstep.htm)
There is also the wiki article: [http://en.wikipedia.org/wiki/SpeedStep](http://en.wikipedia.org/wiki/SpeedStep).  

Start by looking in your bios.  You can also try installing cpufreq on ubuntu:```
sudo apt-get install cpufrequtils
sudo cpufreq-info
```

many thanks^^

i installed cpufreq and when i ran it i got this 

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.60 GHz - 3.07 GHz
  available frequency steps: 3.07 GHz, 1.60 GHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 1.60 GHz and 3.07 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.60 GHz - 3.07 GHz
  available frequency steps: 3.07 GHz, 1.60 GHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 1.60 GHz and 3.07 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GH
```

i also read this article
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/") about CPU scaling. Would this do the same thing as speedstep?And also, is hyperthreading enabled by default, or do i have to still enable it?This might sound stupid but after looking around i found a thread in the Ubuntu Forum Archives saying it is not enabled by default. 

And thanks for the link noobuntu35, that'll be useful when i clean out my computer:grin:

---

### Post by tamoneya on 2008-08-03
that article is pretty helpful.  Although it appears to me as if speed step is already enabled.  You have two steps: 3.07 GHz and 1.60 GHz.  It is also at the lower frequency at the moment which is good.  I think you should start looking more into things like fans and dust right now following noobuntu35's guide.

---

### Post by ilikeroflcopters on 2008-08-03
Mmmk cool. Thanks alot.^^
Just one last thing.Im thinking of testing how fast my computer runs at 1.60Ghz and 3.06Ghz. When i test, should i set both "CPU's" at the same frequency or only change one of them to a different frequency?

---

### Post by tamoneya on 2008-08-03
yes keep them at the same speed.  I dont think you can run them at different speeds though even if you tried so I guess it doesnt matter much.

---

### Post by ilikeroflcopters on 2008-08-03
Ok cool. Thanks alot for all the help^^I really do appreciate it.Especially helping me understand my CPU does hyperthreading, and is not a dual core or anything.

---

### Post by tamoneya on 2008-08-03
no problem thanks for remembering to mark the thread as solved.

---

