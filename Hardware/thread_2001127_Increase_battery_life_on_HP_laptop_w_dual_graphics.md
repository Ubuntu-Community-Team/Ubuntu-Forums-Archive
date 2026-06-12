---
title: "Increase battery life on HP laptop w/ dual graphics"
date: 2012-06-10
forum: Hardware
---

### Post by slowtrain on 2012-06-10
I have a dual boot with Win 7 and Ubuntu 12.04.  The laptop got about 3 times the battery life with Win 7 as with Ubuntu.

I suspect part of that is that Ubuntu is running the Radeon graphics card full-blast, rather than just using or switching to the on-board Intel GPU.  Installation of proprietary drivers via Additional Drivers fails with error messages.  I see no fix available online.  I also tried various tutorials to install Catalyst directly.  This also fails with error msgs and I don't see anyone online suggesting a fix for these errors. 

However, one positive side-effect of partially installing Catalyst seems to be that a) 3D doesn't work, and b) power consumption is down sharply.  I'm guessing I (partially?) disabled the Radeon GPU.  On the other hand, I think I still get about half (75%?) the battery life off Ubuntu than Windows.

Just how much power I'm saving is unclear.  powertop says the battery discharge rate is 25-30 W (watts) when I first start it up, but this quickly shifts to about 19 W and stays there.  Not sure why the change.

I'm wondering if there's anything I can do to improve this situation.  I don't know whether the Radeon GPU is still drawing power--not sure how to find out.  It also seems inelegant and potentially problematic to keep the GPU quiet with a broken version of Catalyst.  Is there a better way to get Ubuntu to just use the on-board GPU, say uninstalling 3D drivers?  Are there any other tricks for reducing power usage (I've played with powertop settings already; got me to 19W; not sure how to make the settings stick.)

---

### Post by N0oki3 on 2012-06-10
Update your BIOS, check inside of BIOS if you can manually switch default graphic card, if you can't (like some of us) than your radeon doesn't work. If you can switch it inside of BIOS than if you want to run unity 3D select discrete GPU and use this [guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)
Otherwise select intergrated gpu [sandy bridge i belive] and do not install manually or via jockey-gtk (additional drivers) fglrx drivers.

For power control I use 
```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

ps: some people say they run better with igpu, some say with dgpu. So ....if you can, try both

---

### Post by slowtrain on 2012-06-13
Hi N0oki3:

Thanks!  I did try switching settings in the BIOS.  I get options of dynamic vs. static graphics.  I gather dynamic means that the needs of applications will determine which card is used.  Static is less clear--presumably something switchable by the user in the OS, but I see nothing in the OS that determines that.

Ubuntu seems to do better with static--a bit less wattage at the low / stable end, and fewer sudden jumps in wattage.  Win 7 gets wacky with static set on--if I don't run into bad video problems, the watts used, according to Joulemeter, jump by about 50%.  I guess I could switch to static for Ubuntu if I know I'm going to need a lot of battery.

I had jupiter installed already.  powertop seems helpful on top of that.

I don't have a clear reading on just how well battery life fares under Ubuntu vs. Windows after all.  The wattage now looks like about 13.3% worse in Ubuntu, if powertop wattage can be compared to Win 7's Joulemeter.  That's not bad.  Then again, what the battery meter says in the two systems isn't entirely consistent.  About 5 minutes after Win 7 starts, the amount of time it says it has remaining on the battery looks to be about 17% better than ubuntu.  About 15 minutes in, it is making claims of getting almost twice the battery life.  Whether that's true or not is hard to say because in actual usage it's closer to the initial reading, but then again, I'm streaming video.  Probably what I should do is compare battery percents after, say 30 minutes of streaming.

---

### Post by mastablasta on 2012-06-14
have you seen this thread?: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
 
if it doens't work it might be good to post some feedback (maybe in the thread) to let others know what model doens't work.

---

### Post by slowtrain on 2012-06-17
Thanks mastablasta!

I'll have to give that a try when I have an afternoon free.  About to leave on vacation, so probably not for a while.

I did discover some instructions for installing and configuring laptop-mode-tools (the configuration info is in the config files, particularly /etc/laptop-mode/laptop-mode.conf).  This should make powertop settings permanent.  Only problem I'm having is that my mouse get auto-suspended and become temporarily non-response--even though I blacklisted suspend for it and powertop doesn't show that the mouse is on autosuspend.  Not quite sure what's responsible for that.  I'm taking jupiter of the system because that seemed to be firing frequently.  My keyboard also seems to be acting up.  Guess I have to play w/ this for a while.

---

### Post by slowtrain on 2012-07-14
A bit of an update.  I've discovered that Ubuntu is MORE energy efficient than Windows, at least on the best test I've run.

I finally had time to run a test to see how much better Windows is in conserving power than Ubuntu for my laptop.  After all, Windows' battery monitor says it will run for (at times) hours longer than Ubuntu says it will.  And the joulemeter in Windows relative to powertop in Ubuntu suggests Windows is consuming 15%-23% less power.

I decided that the time remaining statistic is probably not comparable between the systems because they could be based on very different estimation procedures.  The power usage monitors may also not be comparable because they measure power use from different components.  

I chose to focus on % of battery power remaining because I figure these numbers must be fairly standard, even across systems.

My test involved opening only Chrome and running the same hulu TV show for 30 minutes, not using the system otherwise.  From 15 minutes in till 30 minutes, I collected the % of battery power remaining every 5 minutes.  I then ran a regression analysis on both sets of numbers (from windows and linux) and used that to estimate how much total time I could get out of the battery.  (The regressions fit very well.)

By this estimate, I can get 132 minutes out of Windows and 153 minutes out of Linux, a 16% difference.

Also, with the latest kernel update, my problem with the external mouse getting stuck thanks (most likely) to laptop-mode-tools has largely gone away.  It no longer occurs when the laptop is plugged in, which is when I typically use an external mouse.  It does continue to occur with the laptop unplugged.

---

