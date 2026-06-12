---
title: "Help needed: CPU fan will not slow down"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by mibs on 2007-03-14
I'm sure many of you have seen this asked before. I've searched the forums for threads on this but all I could come up with were threads with no replies or answers that didn't seem to do anything.  When I run windows I can barely hear my computer, but the moment I boot up Ubuntu (edgy) my cpu fan starts spinning much faster, creating a lot of noise.  It then continues to spin, and it cycles between very and and very loud to moderately fast and moderately loud.  Even when my cpu is idle the fan does this.  It is quite annoying when there is no sound around me except the fan running at full tilt.  I've read some things about lm-sensors, tried the how-to on that but couldn't get anything.  I read about powernowd but wasn't sure if i should install it or not.  So what I'm asking is, does anybody know what causes this issue? and is there a solution to it, because I cannot seem to find out.

my cpu is a pentium 4 3.06 GHz.  I can supply any other required information if necessary.

Thanks for any help.

---

### Post by jellyfisharepretty on 2007-03-14
Wow, this happened to me too, except I don't remember completely how I fixed it :shock: 

Never had much luck with lm-sensors.

First, check your BIOS options, modern motherboards have options for enabling / disabling automatic fan control.  Or you might be able to specify a constant fan speed that's not so loud (don't overheat your CPU though).

I know you have an Intel, but with my AMD I turned on cool & quiet.  I think the intel equivalent is SpeedStep, not 100% sure.

It's also possible that it's you video card making all that noise.  My nvidia card was very loud all the time in linux before I installed the binary nvidia drivers.

---

### Post by mibs on 2007-03-14
I originally thought it was the video card.  I have an ATI Radeon x1900gt and I thought it was that.  I ruled that out the other night by taking the card out and booting up.  I still got the extreme fan noise, so it coulnd't be the video card.

---

### Post by Death_Sargent on 2007-03-15
Are you using the proper drivers for your video card 

Mesa = pore hardware usage = heat = fan always on

Your going to want to follow the instructions on how to Disable aigxl and composite manager(compiz) if you are using these that is part of the problem.

Also you should check to see if acpid is in the startup run level. 

Also I would recommend using a vacuum to clean out your intake fans (JUST TRUST ME) takes about 30 mins on my laptop to effectively clean it out

---

### Post by mibs on 2007-03-15
I'm not using compiz or beryl. Like I said earlier I physically took out my video card and booted ubuntu, and I still had the problem which rules that out.  

I regularly take apart my computer and clean all the fans and dust, so that's not an issue.  Like I said I don't have this problem on windows.

I'll see about acpid.

Thanks for the replies.

---

