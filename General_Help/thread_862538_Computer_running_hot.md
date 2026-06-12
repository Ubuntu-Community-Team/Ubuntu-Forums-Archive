---
title: "Computer running hot"
date: 2008-07-17
forum: General Help
---

### Post by whitecountess on 2008-07-17
I recently upgraded to Hardy and have been having issues with my computer running hot. I wasn't the one who did the upgrade (I had my ubuntu nerd do it for me) -- but after the install, it was running extremely hot, to the point of randomly shutting down. He did some fixes, and it's helped -- but the computer is still running hot.

Just idling, my CUP temp sits around 44° C but the GPU sits at about 69° C. I've yet to hear my internal fans come on and the moment I do something graphics card intensive (IE - World of Warcraft) the GPU temp will spike anywhere between 80° C and 90° C. This... doesn't seem normal to me.

On top of that, while my cpu scaling is set to 'on demand', it doesn't change from 800MHz and I know it will scale up to 1.6MHz. Even if I select 1.6MHz, it stays at 800MHz. 

While the computer runs decently, I'm concerned with how hot it's getting.

---

### Post by silkstone on 2008-07-17
No, the GPU shouldn't get that hot.

Have you installed lm-sensors? I'm not familiar with setting it up, but it may work without much configuration and help to control the fans.

---

### Post by kuja on 2008-07-17
What model is the GPU? Some of those things run fairly hot or so I'm read. Mine idles at around 55C, but I've got a passive cooler on it.

CPU being in the 40's is okay, that won't hurt anything. GPU in the 90's though could be bad. You should probably try to get some airflow around it (clean up cables, add a fan near it, replace the GPU heatsink/fan, stuff like that)

---

### Post by bodhi.zazen on 2008-07-17
The most common cause of over heating is a dirty environment.

Open your box an clean it. Make sure all your fans are working.

---

### Post by whitecountess on 2008-07-17
Unfortunately, it's a laptop, so just opening the box isn't as much of an option.

---

### Post by f37u5g0d on 2008-07-17
Log onto windows and check your temperatures to see if ubuntu isn't controlling the fans right or if your fans are getting old and slow / have burned out completely.

---

### Post by whitecountess on 2008-07-17
> **f37u5g0d said:**
> Log onto windows and check your temperatures to see if ubuntu isn't controlling the fans right or if your fans are getting old and slow / have burned out completely.

That's the weird thing. Under Gutsy? Everything functioned just fine. The fans would kick on and the CPU scaling would function properly. Now, I've upgraded to Hardy and what -was- working, isn't now.

---

### Post by bodhi.zazen on 2008-07-17
> **f37u5g0d said:**
> Log onto windows and check your temperatures to see if ubuntu isn't controlling the fans right or if your fans are getting old and slow / have burned out completely.

Actually, you can usually collect this information from the BIOS.

---

### Post by f37u5g0d on 2008-07-17
Try lmsensors.  I've never been able to get it to work but I've also never really tried that hard.  Cleaning the case is also a good idea.  If it really is the operating system's fault you would have noticed a very sudden change.  If it is dirt then the problem would have been gradually getting worse and will probably continue to worsen until the case is cleaned.

---

### Post by rmjohnson144 on 2008-07-17
It sounds like your video card is overheating.  It is very common lately especially if it is an ATI chipset.  Not sure if you get options to control the fan speed outside of Windows.  You may need to find if there is an option in your control panel or drivers to change fan speeds.  I don't know of any video card over clocking programs for Linux that would be able to give you this option.  Since I'm just returning to Linux after a long while maybe someone knows of a good utility to do this.

-=Mark=-

---

### Post by kuja on 2008-07-18
> **whitecountess said:**
> Unfortunately, it's a laptop, so just opening the box isn't as much of an option.
Just get into any areas you can and clean those out. (there are generally several access panels on the bottom, you'll need a screwdriver probably.) With regards to it "not being doable", of course it is ... it just might take a fair amount of effort.

---

