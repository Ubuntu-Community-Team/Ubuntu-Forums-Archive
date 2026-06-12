---
title: "CPU scaling - ongoing joke of Ubuntu"
date: 2008-05-01
forum: Hardware
---

### Post by Brinstar on 2008-05-01
Why is it such a big deal to get scaling working under Ubuntu? Why does something that works first time under winxp take so much effort for the Ubuntu dev team to get right? 

I have always had to configure cpufrequtils by hand to stop the fan from working overtime unnecessarily. Why can't this simple task be done for the user. I was really hoping that this would have been solved by the release of Hardy about 4 years after i first used Ubuntu. I'm obviously expecting too much!

Even setting cpufrequtils now doesn't bring the cpu down to the speed where the fan doesn't need to run so high. The snap-in panel tells me its running at a constand 798mhz, compared to 275mhz in winxp. so now it doesn't even work up to the point that it worked in 7.10 ](*,) do the devs hate me? :cry:

---

### Post by lumpymayo on 2008-05-01
Kind of funny, I was just starting to get annoyed at my CPU fan for running so fast for no reason at all when I saw this. Do you know of a way to get this fixed? If you do, can you please explain to me what to do?
I'm fairly new to Linux so I wouldn't be able to figure it out myself

---

### Post by Brinstar on 2008-05-02
> **lumpymayo said:**
> Kind of funny, I was just starting to get annoyed at my CPU fan for running so fast for no reason at all when I saw this. Do you know of a way to get this fixed? If you do, can you please explain to me what to do?
I'm fairly new to Linux so I wouldn't be able to figure it out myself

what *used* to work for me was to install cpufrequtils and set the ondemand governor to run at boot. sorry if this is complicated, but read the manuals and you should be able to work it out.

however i still can't seem to get any of the cpu scaling daemons to scale the cpu down to 275mhz, which is possible under WinXP. someone must know why this isn't possible?? 

I am actually thinking of going back to xp at this point, especially after the release of SP3.

---

### Post by boppp on 2008-05-02
Damn, got the same thing here. I am getting crazy of that FAN sound, i do have conservative (or ondemand) configured.

applications->system tools->configuration editor, and then search (ctrl+f) for 'cpu', it's the first one i think. You can put in your own thing, but not the processor speed.

My processor is running 50% but the fan is _still_ making overtime, _even_ when my CPU temperatures are 66 degrees celcius and 68 degerees celcius.
IF there is some fix for this (even if this means lower cpu speed) i would really appricitate this, cause there is only so much fan noise i can take a day!

---

