---
title: "HP dv7 overheating whenever put in sleep mode!"
date: 2012-08-05
forum: Hardware
---

### Post by blackwolf92 on 2012-08-05
Hey!
I am running Ubuntu 12.04LTS on my HP Pavilion dv7 laptop and one annoying problem i have is that whenever my computer is set to sleep and the display goes off, it suddenly overheats and the fan runs crazy! Same thing happens when i'm watching Youtube videos. I installed Psensor and monitored the temperature of the laptop and in the two previous cases it is getting as high at 99 degrees celcius (which is extremely annoying!).

Is there any relation between my Graphics card and this overheating problem? Is there any missing drivers or a way to fix it? 

I recently noticed that the Graphics info displayed (when i navigate to System Settings > Details) shows VESA:MADISON.
Running lspci | grep VGA in terminal:
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

Is this overheating normal? Any solutions/suggestions?
Your help is much appreciated!
Thank You!

---

### Post by jnedenrod on 2012-08-05
I know I read somewhere on these forums that Ubuntu 12.04 cannot come out of sleep mode, but I suppose I'll leave that to the Ubuntu experts.

As for the overheating, I have an HP Pavilion dv6 myself and had it overheat a few months ago.  If you know how, take the computer apart and clean the fans.  HP was kind enough to make it so you have to take apart the ENTIRE laptop to get to the fans... grrr!  Since mine overheated, I started using a slightly elevated tray with two external fans.  Obviously, this gets more air into the system to cool it, but it also helps prevent particles from getting into the system.

As with any laptop, always try to put it on a hard surface and if you must put it on your lap, (after all, it is a "laptop") do so in short intervals and try to avoid dust.  Hair from pets can cause overheating rather quickly.  I always take the battery out and run it via AC power.  The battery can get quite hot if it's plugged in.  Just be sure you don't accidentally unplug it, and try to keep the AC cord away from any foot-traffic.

---

### Post by blackwolf92 on 2012-08-05
> **jnedenrod said:**
> I know I read somewhere on these forums that Ubuntu 12.04 cannot come out of sleep mode, but I suppose I'll leave that to the Ubuntu experts.

As for the overheating, I have an HP Pavilion dv6 myself and had it overheat a few months ago.  If you know how, take the computer apart and clean the fans.  HP was kind enough to make it so you have to take apart the ENTIRE laptop to get to the fans... grrr!  Since mine overheated, I started using a slightly elevated tray with two external fans.  Obviously, this gets more air into the system to cool it, but it also helps prevent particles from getting into the system.

As with any laptop, always try to put it on a hard surface and if you must put it on your lap, (after all, it is a "laptop") do so in short intervals and try to avoid dust.  Hair from pets can cause overheating rather quickly.  I always take the battery out and run it via AC power.  The battery can get quite hot if it's plugged in.  Just be sure you don't accidentally unplug it, and try to keep the AC cord away from any foot-traffic.

I read a while ago about cleaning the fans but i didn't do it because as u just mentioned, you have to take apart the whole thing so that you can clean it.. I think i have to try this sometime soon!
I use a cooler pad most of the time, it keeps the laptop a bit cooler but doesn't solve the problem.

Thank you for your reply, much appreciated!

---

### Post by jnedenrod on 2012-08-05
Apparently, I'm becoming closer to an Ubuntu expert by the hour.  Regarding Ubuntu not being able to come out of sleep mode: I believe sleep mode is not supposed to be a problem for Ubuntu.  However, sleep and hibernate modes can be problematic if you're not set up correctly.  It has to do with running out of memory. You need a second partition for swapping.

Brush up on swap here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Then read this thread. There's even a formula for calculating how much swap you need for your system: [http://askubuntu.com/questions/103242/is-it-safe-to-turn-swap-off-permanently](http://askubuntu.com/questions/103242/is-it-safe-to-turn-swap-off-permanently)

---

