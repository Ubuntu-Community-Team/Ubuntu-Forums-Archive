---
title: "Powersaving on server?"
date: 2009-04-07
forum: Hardware
---

### Post by mathiasi on 2009-04-07
I recently installed a minimal ubuntu installation on my Asus Eee 900. Supposed to be the server edition, but the kernel is "Linux 2.6.27-11-generic", not sure why it not the server edition, but that doesn't matter. 
It's primarily used as a webserver, running apache, mysql etc. 24/7 

But is there someway to install somekind of powersaving feature ? The CPU is constantly running at 900Mhz - Anyway to automaticly step it down and then up when it's stressed ? 

I know when I first booted up the system with Asus' standard version of linux the power consumption was around 15 Watt but now it's 25 Watt - So is there any packages that I can install to bring it down without affecting the performance too much?

---

### Post by sdennie on 2009-04-07
There are many ways to save power but none of them are enabled by default in Ubuntu (though, the ondemand governor is for supported machines.  Is 900Mhz the max or min speed?  It should already be acting the way you want in that regard).  This site is great for learning about it: [www.lesswatts.org](www.lesswatts.org).  This is what I personally use and, though it's not related to your server (and it's for a laptop), it describes how to implement the things talked about at LessWatts and has a few other tricks: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by mathiasi on 2009-04-07
> **sdennie said:**
> There are many ways to save power but none of them are enabled by default in Ubuntu (though, the ondemand governor is for supported machines.  Is 900Mhz the max or min speed?  It should already be acting the way you want in that regard).  This site is great for learning about it: [www.lesswatts.org](www.lesswatts.org).  This is what I personally use and, though it's not related to your server (and it's for a laptop), it describes how to implement the things talked about at LessWatts and has a few other tricks: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

900Mhz is the max. Thanks for the link - I'll take a look at it. What I want it to do is clock down the CPU when it's not loaded - My average load is somewhere around 5% so I don't mind clocking down the CPU as long as it automaticly clocks up again, when it's necessary.
Another thing I have wondered about is why I dont have a "/sys/devices/system/cpu/cpu0/cpufreq/" or "/proc/cpufreq" folder - The CPU is a Pentium M so it should be compatible with CPU scaling.

---

### Post by mathiasi on 2009-04-07
Hmm it may seems like the Eee PC series is not fully compatible with the generic kernel in 8.10 - I've seen posts where people advice to install the array kernel ( [http://www.array.org](http://www.array.org) ) - Could that may solve my problem ?

From the site: *The asus_eee module provides support for manipulating the front-side bus (FSB) for overclocking, fan override, and monitoring the system core temperature and fan's speed.* ( [http://www.array.org/ubuntu/asus_eee.html]("http://www.array.org/ubuntu/asus_eee.html") )

---

