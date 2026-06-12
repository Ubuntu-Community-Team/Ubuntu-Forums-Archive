---
title: "laptop-mode even when on power line to cool down the machine"
date: 2009-11-11
forum: Hardware
---

### Post by joao_da_costa on 2009-11-11
Hi, guys!

I have been using ubuntu since 7.04 version and I am greatly happy with it. :) 

I installed the 9.10 one in my recently acquired laptop and it worked perfectly in general. Now I am trying some settings to extend battery life and also make it cooler. I don't wish severe settings that could damage hardware of course. So I have watched [LessWatts.org]("http://www.lesswatts.org") and picked up some configuration settings. *Powertop* command is always with me. :)

The problem: I use *cpufreq* and *cpu frequency scaling monitor* to set *powersave* mode. That works nicely when out of power line. My cpu supports speedsteps of 1.2, 1.6, and 2.0 GHz. Whith AC off, *cpufreq *always accept my configuration of *powersave* and 1.2 GHz. But once my battery gets drained and I plug AC, the frequency goes to 2.0 GHz and, no matter what I try, it does not go down to the cooler 1.2 GHz.

The question: How should I proceed to turn laptop-mode on even when connected to power line?

Thanks in advance! :)
Joao

---

### Post by Remczas on 2009-11-11
```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```
and find sth like this
```
ENABLE_LAPTOP_MODE_ON_AC=0
```
change 0 to 1

---

### Post by joao_da_costa on 2009-11-16
> **Remczas said:**
> ```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```
and find sth like this
```
ENABLE_LAPTOP_MODE_ON_AC=0
```
change 0 to 1

I had this variable set to 1 already but it didn't work. 

I manage to make it work through the tips I found here:
[http://ubuntuforums.org/showthread.php?t=944190](http://ubuntuforums.org/showthread.php?t=944190)

Well, I have tried a lot of different solutions but I think the solution was indeed the ideas mentioned in the thread above.

Thanks anyway, Remczas

---

