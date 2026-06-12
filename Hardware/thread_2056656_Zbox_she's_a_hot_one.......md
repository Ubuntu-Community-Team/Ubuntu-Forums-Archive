---
title: "Zbox she's a hot one......"
date: 2012-09-11
forum: Hardware
---

### Post by afulldeck on 2012-09-11
I'm running ubuntu 64bit on a the zotac zbox nano AD11 as my entertainment unit. However, I'm finding she is running hot with no real activities other than web browsing. I'd like to cool her down, if that is at all possible. Anyone know or have an insight on these boxes and Ubuntu?

---

### Post by afulldeck on 2012-09-12
Bump. I guess not many of you have used the Zboxes? Probably bad pick on my part......

---

### Post by Ubunterrific on 2012-09-12
> **afulldeck said:**
> Bump. I guess not many of you have used the Zboxes? Probably bad pick on my part......

Power management and overheating is becoming an increasingly popular topic lately. I can only offer suggestions like pulling out packages you don't use, updating everything, maybe compile your own kernel etc
However, i have a lot of success using Jupiter. It's a little applet that sits on the panel and tells you the processor temperature and allows you to switch between Power saving, on demand and performance. Basically, it forces your processor to operate at a lower frequency and sets things to save power and not operate so hot.
Bit of a knock to performance is expected, but it can mean the difference to a drop of 15 or so degrees for me, which is significant.

There are lots of things you can do, really. Lots of commands to set things to go into power saving mode etc. Have a look at powertop as well - it tells you what's using the most resources, how much power it's using overall and any tweaks you can do to set things into low power mode etc

---

### Post by afulldeck on 2012-09-12
> **Ubunterrific said:**
> Power management and overheating is becoming an increasingly popular topic lately. I can only offer suggestions like pulling out packages you don't use, updating everything, maybe compile your own kernel etc
However, i have a lot of success using Jupiter. It's a little applet that sits on the panel and tells you the processor temperature and allows you to switch between Power saving, on demand and performance. Basically, it forces your processor to operate at a lower frequency and sets things to save power and not operate so hot.
Bit of a knock to performance is expected, but it can mean the difference to a drop of 15 or so degrees for me, which is significant.
 
There are lots of things you can do, really. Lots of commands to set things to go into power saving mode etc. Have a look at powertop as well - it tells you what's using the most resources, how much power it's using overall and any tweaks you can do to set things into low power mode etc
 
Thanks, that is helpful.  I'm assuming  that both Junipter and powertop are in the USC? Or a PPA somewhere else?  I'll check once I'm back to home base on Friday. Thanks again....

---

### Post by Ubunterrific on 2012-09-12
> **afulldeck said:**
> Thanks, that is helpful.  I'm assuming  that both Junipter and powertop are in the USC? Or a PPA somewhere else?  I'll check once I'm back to home base on Friday. Thanks again....

**```
sudo add-apt repository ppa:webupd8team/jupiter**
sudo apt-get update
sudo apt-get install jupiter
```

for jupiter and powertop should be in the repos.

Have a look into what's causing wakeups for you computer. The command 'top' in a terminal will show the processes using the most resources too - investigate. People have had these problems in the past because of a less than friendly kernel and there *have  *been power regressions every now and then and interprocessor scheduling hangs etc

---

