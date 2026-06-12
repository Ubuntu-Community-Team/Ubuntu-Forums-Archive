---
title: "Laptop Power Consumption After Sleep Significantly Increased"
date: 2010-06-05
forum: Hardware
---

### Post by anon2122 on 2010-06-05
Dear all,

  	 	 	 	 	 	  I installed Ubuntu 10.04 x64 on my new laptop (Acer TravelMate Timeline 8371). It's a high-spec CULV laptop, and gets around 7-8 hours battery life under light usage in Windows 7.
 

 I am getting even better battery life in Ubuntu (suggestions of 9 hours+, in fact Ubuntu has suggested 9hrs30mins on occasions. I believe this estimate is correct, since Ubuntu seems to be a much leaner OS than Windows 7.
 

 To explain my system config (as it's not too common) – this laptop has two graphics chips. An Intel 4500MHD integrated chip for low power consumption, and an ATI Mobility Radeon 4330 for casual gaming/3D graphics work etc. Out the box, Ubuntu was only going to get 2 hours battery life, since it was not disabling the unneeded card.
 

 I compiled a 2.6.34 kernel with the new vgaswitcheroo enabled, and used instructions online to create an 'interface' to it, which allows the card to be switched, and power to the cards controlled.
 

 My own modification was to add to init.d a few power saving commands suggested by powertop, in addition to my own commands to enable Intel graphics by default, and power down the ATI chip.
 

 This works fine most of the time, and I can get my 9+ hours of estimated battery life out the laptop under light/minimal usage.
 

 The issue comes with sleep. I managed to get sleep to work using the  i8042.reset=1 addition to grub (See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120) for the bug report).


But when I resume for sleep, my battery life estimate and power consumption both dramatically worsen. For example, before sleep, powertop reported my power consumption as 6.8W (10 hours 30 mins remaining), yet after sleep I was only expected to get 4.4 hours with it running at 14.8W :(


I think after resuming from sleep, the fan turned itself on and wouldn't disable, although I can't be sure that's the only issue. My kernel appears to be fine, and the second graphics card seems to be staying off fine (only 2.5 hours battery if it comes on, so it's not that)


So... anyone got any ideas about the power consumption after sleep? I am not sure what logs would help, but if there are any, give me a shout and I'll get them.


Also, where is the best place to run commands I want executed as the root user at boot? I would like to add all the powertop recommendations to something to execute them at boot (mainly the ondemand governor, as that really helps the power consumption by allowing the CPU to underclock to 800 MHz instead of 1.4GHz).


Finally, while I'm here, are there any other tweaks or patches I should apply to optimise power consumption, as I'm new to running ubuntu on real hardware, although have used it a bit in Virtualised Applications?


Regards

---

### Post by Sonador on 2010-06-06
Hi, is there a process **vbetool** running after resume from sleep (did you mean suspend?), because this process consume ~98% of my CPU after resume from suspend.

---

### Post by anon2122 on 2010-06-06
> **Sonador said:**
> Hi, is there a process **vbetool** running after resume from sleep (did you mean suspend?), because this process consume ~98% of my CPU after resume from suspend.

Hi,

You are indeed correct that I refer to suspend to RAM (ie. S3 state).

I checked ps and this process exists both beforeand after suspend, but it is using 0% CPU on both occasions. Top reports minimal CPU usage at all times too.

The increase in power use is huge, with it doubling to 16W from 6 to 8 W.

Something is making me suspicious of the i915 graphics driver,  but I don't know how to even look at tracing this.

[http://www.google.co.uk/m/search?q=I915+power+consumption+after+resume&aq=f&oq=&aqi=-k0d0t0&fkt=2760&fsdt=33384&csll=&action=&ltoken=dd97289893305](http://www.google.co.uk/m/search?q=I915+power+consumption+after+resume&aq=f&oq=&aqi=-k0d0t0&fkt=2760&fsdt=33384&csll=&action=&ltoken=dd97289893305)
I found this on Google though; 

I'd really like to stick with ubuntu, as it seems amazingly more efficient than win 7, but this is stopping me using it just now :(

Thanks for the suggestion though.

Regards

---

### Post by anon2122 on 2010-06-06
Hmm. Been researching this further, and it seems that similar issues have existed for a long time (Since 2007). If this is the case, I guess ubuntu isn't for me... Maybe I'll need to find a more up-to-date distro :( I thought my custom kernel should have fixed any kernel level bugs not resolved in .33, but evidently not.

Thanks for the help though. I'll keep an eye out here for a few days while I try and find another distro without the problem. Maybe gentoo or fedora. Not sure...

Cheers

---

### Post by Marc128000 on 2011-01-17
I did some testing and posted the results in my blog. On my HP Envy 14 I am seeing about a 20W INCREASE after a suspend.
Blog post is here: [http://linuxenvy.blogspot.com/2011/01/battery-life-review.html](http://linuxenvy.blogspot.com/2011/01/battery-life-review.html)

---

### Post by nicocarbone on 2011-12-29
Sorry for bringing this post back after so long, but I think I found the problem and a possible workaround.

I have a HP Envy 14 laptop with switchable graphics, and I had the problem described in this thread. I even file a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/909337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/909337)

After some test, I think I identified the problem. After resuming from sleep, the discrete GPU turns on, despite vga_switcheroo saying it is OFF. Turning ON and then OFF again the discrete GPU (more correctly, the unused GPU) solves the problem. 

In order to do this, I created this script, located in /etc/pm/sleep.d/ and named 00_hybrid_graphics

```
#!/bin/sh

case "$1" in
    hibernate|suspend)
        ;;
    thaw|resume)
	echo ON > /sys/kernel/debug/vgaswitcheroo/switch         
	sleep 45	
	echo OFF > /sys/kernel/debug/vgaswitcheroo/switch 
        ;;
    *)
        ;;
esac

exit 0
```

This script runs on resume and applies the workaround. I don't know if this is the best way of doing this, though.

---

