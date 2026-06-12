---
title: "black screen after suspend, Eee PC 1101HA (GMA500/Poulsbo), 10.4"
date: 2010-11-06
forum: Hardware
---

### Post by cr0m on 2010-11-06
After a lot of fruitless searching, I'm starting my own thread. I'm running 10.4 (lucid) on an ASUS Eee PC 1101HA (GMA500/Poulsbo).

I have the Poulsbo drivers installed and have no video problems (so far). When I suspend using the Fn + F1 key and wake up the laptop, I get a black screen with no cursor, etc. It *looks* like the xserver isn't coming back up, but that's wild speculation.

Can anyone help me troubleshoot? I also need advice about either of the two fixes mentioned here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks)

*edit:* I haven't installed any of the updates I'm being prompted to install by the update manager. Partly this is because I haven't had the time to plug into AC power and do the 300Mb of updates. Partly this is because I generally follow a policy of "if it ain't broke, don't fix it", and don't like to blindly update software.

---

### Post by cr0m on 2010-11-07
Update: I installed the updates. I also did the 2nd tweak mentioned on the wiki page above. (Speaking of which, I think there's a typo in the instructions... /etc/pm/config/defaults should be /etc/pm/config.d/defaults).

Now I'm able to suspend, but it's pretty disappointing. Because I have to open a terminal and sudo to suspend, it means the laptop isn't too useful for the non-technical folks in my life.

Can anyone point me to a page with some background on the issue? I'd like to get my head around what the problem is.

---

### Post by cr0m on 2010-11-08
Well, I did some reading in the massive [Guide to Get the Best Performace from the GMA 500]("http://ubuntuforums.org/showthread.php?t=1229345") thread and have a somewhat better handle on the relationship between the video card and the various suspend/hibernate problems.

I also tried the first tweak mentioned in the thread I linked to in my first post (ie moving /usr/lib/pm-utils/sleep.d/99video). My suspend button (Fn + F1) still has the same issue, as does suspending the machine by closing the laptop.

If anyone knows whether these two tweaks are mutually exclusive, or has any advice on this issue, I would greatly appreciate the help.

I would also like to ask the wiki community to work on condensing the advice in the GMA500 thread into one or more wiki pages. As it is, the thread is extremely difficult to use, even with the "search thread" function.

---

