---
title: "my laptop overheats"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by forevertheuni on 2007-08-21
Hi all ..my asus a8js overheats and shut downs if the cpu's run at 2ghz at 100% for a lot of time. The thing is I wanted to put a temp threshold so that it has a maximum(that I wanted to set) frequency. I know that in cpufreqd I could do this. However I don't know what ubuntu uses for power management. Is there an easy way in the scripts?
Tnx
João

---

### Post by tommy18crowe on 2007-08-21
Well, one good idea is to keep it at maximum power and then get a laptop cooler from a staples or Office Max, or Best Buy's or some computer place, even wal-mart has them. They work great. I'm not sure what else to do about your scripts though.

---

### Post by forevertheuni on 2007-08-21
> **tommy18crowe said:**
> Well, one good idea is to keep it at maximum power and then get a laptop cooler from a staples or Office Max, or Best Buy's or some computer place, even wal-mart has them. They work great. I'm not sure what else to do about your scripts though.

EU guy not US! But..I don't want to buy a laptop cooler. Because if I set the cpu freq to 1.3Ghz it never overheats. I wanted a software solution.

---

### Post by Mr_Mason on 2007-08-21
have you overclocked it to 2ghz from something else or does it run at 2ghz normaly?
Laptops do overheat loads how do you use your laptop is it on a hard flat surface?

---

### Post by forevertheuni on 2007-08-21
> **Mr_Mason said:**
> have you overclocked it to 2ghz from something else or does it run at 2ghz normaly?
Laptops do overheat loads how do you use your laptop is it on a hard flat surface?

No.It's 2ghz standard. But probably in windows it downclocks auto with software or something(can't say..I scrapped it from disk and ask for money refund).
I usually lift the laptop so that the intake and out fans are clear.

---

### Post by billy420 on 2007-09-30
My laptop overheats too, but didn't want to make a new laptop overheating thread since I can see there are already many of them.

My laptop didn't overheat untill recently, when I switched up my OS a few times between slackware/freebsd/debian.  Got less than zero cash to spend these days on extra computer equipment, so I too am looking for a software solution.

Is there a way to limit the clockspeed on my CPU or something?

Any assertations/suggestions will help.

---

### Post by Rokashevich on 2007-10-07
I had the same problem and wrote a small daemon that changes CPU governor to powersave when its temperature reaches 65C (i have thinkpad t60) and sets governor back to performance when t falls down to 50C

So if u want i can give you sources.

---

### Post by Rokashevich on 2007-10-07
and what do u think, how is it ideologically more correct to realize this feature: as a separate deamon watching cpu temperature and applying appropriate governors or to realize it in kernel space as a part of laptop-mode-tools?

---

### Post by dinub1 on 2007-10-07
> **forevertheuni said:**
> EU guy not US! But..I don't want to buy a laptop cooler. Because if I set the cpu freq to 1.3Ghz it never overheats. I wanted a software solution.

Have the ktemperature module installed and running. This will report  your CPU temp.

$ sudo apt-get update
$ sudo apt-get install ktemperature
$ ktemperature

Then lower your CPU freq, see what happens.

$ sudo cpufreq-selector -g powersave

This should reduce your CPU frequency to approx 1/3 of its full speed.

When you need your full CPU power type:

$ sudo cpufreq-selector -g performance.

This will set up your CPU freq to full.

There seems an issue with CPU power regulation (not voltage, but frequency) in latest Ubuntu editions, notably 7.04 and 7.10.

---

### Post by dinub1 on 2007-10-07
> **Rokashevich said:**
> and what do u think, how is it ideologically more correct to realize this feature: as a separate deamon watching cpu temperature and applying appropriate governors or to realize it in kernel space as a part of laptop-mode-tools?

Kak Zdarovyia :) ?

---

### Post by Rokashevich on 2007-10-08
Ah-ha, and ship all kde-libs, no, thanks)

---

### Post by Rokashevich on 2007-10-08
dinub1, how do u do? =)

---

### Post by billy420 on 2007-10-15
> **dinub1 said:**
>  ... comment about ktemperature... 


Thanks- this is very helpful. :cool:

---

### Post by dinub1 on 2007-10-16
Billy420: you are welcome.

---

