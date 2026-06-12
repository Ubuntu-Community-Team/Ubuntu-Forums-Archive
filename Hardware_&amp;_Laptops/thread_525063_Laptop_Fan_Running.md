---
title: "Laptop Fan Running"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by aeleneski on 2007-08-13
I have an HP Pavilion zv6000 laptop and I have noticed that my fan on it constantly is running. From the moment I power the machine on, it is going at full speed. Even if I leave the laptop sitting there, it never slows down. Now my power settings are set at dynamic, and I do see the speed of the processor at 1 ghz most of the time, with it scaling up towards 2 ghz at times of load. What could be causing this problem? And is there any solution?

---

### Post by scrooge_74 on 2007-08-13
You should research a little, I have one of those nx6110 and I get a similar problem, the system does not cool itself enough for it to stop, I did some research about scalling the processor and it workd sometimes.  The sound is anoying.  I do like my wife's T43 is a lot more quite.

---

### Post by benhagerty on 2007-08-13
I have a similar problem as well. 

/bumpie

---

### Post by dj Kalma on 2007-08-14
I also have similar issues. I've got an HP Compaq nc8430 as my home laptop and the fan just won't stop. Ever. I've gotten quite used to it but if someone could point me to some direction on how to minimize the noise, I'd be very grateful.

---

### Post by Jukka-Pekka on 2007-08-14
I also have the nc8430 from HP. 

Symptoms: Fan running constantly, far less battery life than with windows and much more heat. Processor seems to scale only between 1 and 2 GHz with no intermediate steps (1.33&1.66).

I have used several evenings researching this power problem.
Unfortunately there seems to be no solution readily available. In windows, there are several programs available for laptop configuration... In the Linux world, this does not seem to be the case. But as laptops become more and more popular - as the trend shows- these heating problems become more and more widespread in Linux, Ubuntu included.

There seems to be something happening with 7.10 (gutsy), but as i read the specs it may be only for "mobile devices" less capable than modern laptops. Hopefully the power management features will be enhanced for laptops as well in the near future. Either as included in Ubuntu or as an additional, downloadable and easily installable feature.

One solution that works is to compile a custom kernel optimized for your processor etc., (there are instructions available in the net) but that is not a very lucrative proposition for anyone as "new" to linux as i am. So, a no-go there as well.

One thing to try is to include the CPU-clock applet in your "taskbar", with this you can manually change processor speed. (Click right mouse button with cursor on a taskbar - then add to panel - choose the CPU-applet)

Best regards,
Jukka

---

### Post by dj Kalma on 2007-08-14
Thanks, Jukka, for your reply. You confirmed my suspicions about this matter. I'll give that applet-thingy a go this week, since its the only viable solution at this point.

---

### Post by scrooge_74 on 2007-08-14
> **Jukka-Pekka said:**
> I also have the nc8430 from HP. 

Symptoms: Fan running constantly, far less battery life than with windows and much more heat. Processor seems to scale only between 1 and 2 GHz with no intermediate steps (1.33&1.66).

I have used several evenings researching this power problem.
Unfortunately there seems to be no solution readily available. In windows, there are several programs available for laptop configuration... In the Linux world, this does not seem to be the case. But as laptops become more and more popular - as the trend shows- these heating problems become more and more widespread in Linux, Ubuntu included.

There seems to be something happening with 7.10 (gutsy), but as i read the specs it may be only for "mobile devices" less capable than modern laptops. Hopefully the power management features will be enhanced for laptops as well in the near future. Either as included in Ubuntu or as an additional, downloadable and easily installable feature.

One solution that works is to compile a custom kernel optimized for your processor etc., (there are instructions available in the net) but that is not a very lucrative proposition for anyone as "new" to linux as i am. So, a no-go there as well.

One thing to try is to include the CPU-clock applet in your "taskbar", with this you can manually change processor speed. (Click right mouse button with cursor on a taskbar - then add to panel - choose the CPU-applet)

Best regards,
Jukka

Form me I was advice to use gfreglet and install a few other things I dont remember, the results are mix.  

Compiling a stock kernel could prove useful, I just haven't gotten around to that yet, I may try that on the weekend when I have more time

---

### Post by dj Kalma on 2007-08-15
Hi all, just a quick update on my situation: I messed around with various CPU frequency scaling techniques and managed to get it to work. Both of my cores are now registering as 1 GHz in the CPU Frequency Monitor, when I've set the scaling governor as "ondemand". That's as low as they can go, but still the fan is making noise and the heat just keeps on rising. It's not dangerous to the computer (at least hasn't been for now), but still it annoys me.

Is this just something I have to deal with while using this computer model or is it likely that some future Ubuntu releases will tackle this problem?

---

### Post by shad0w_walker on 2007-08-15
Have you tried installing 'powersaved' from the repos? I have heard a few people with this problem have installed this and sorted it out.

---

### Post by dj Kalma on 2007-08-15
> **shad0w_walker said:**
> Have you tried installing 'powersaved' from the repos? I have heard a few people with this problem have installed this and sorted it out.
Hi, I did install it now and from what I gather, it's just another way of setting the CPU frequency plus other power management stuff. 

The scaling works nicely at the moment on my laptop, but 1GHz is as low as it will go, at least according to cpufreq-info:

> $ cpufreq-info
cpufrequtils 0.4: cpufreq-info (C) Dominik Brodowski 2004
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: centrino
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 2.00 GHz


I'm still a bit baffled because of the fan spinning and heat buildup of my laptop. I just can't understand why the machine heats up so badly. If my memory serves, it has always been like this (>1 year), so I don't think the insides of the machine are that badly clogged.

---

### Post by scrooge_74 on 2007-08-16
It says I can't use powersaved because I dont have a centrino

---

### Post by Jukka-Pekka on 2007-08-17
That's the way things are on my nc8430.

The processor never goes under 1 GHz, but that's the way Intel designed these. For heat generation, the voltages supplied to the processor are also important.

In windows, there are several programs (e.g. NHC, Notebook Hardware Control) with which to alter the settings to get temperatures (and, therefore, the annoying fans!) lower. And battery time up. 
In Linux, no such thing exists yet. For us "mere mortals", that is ;)

All the best - still searching for a solution

Jukka

P.S. i have started exploring gutsy gibbon, the next release of ubuntu. No improvement there yet, but will look into it further.

---

### Post by dj Kalma on 2007-08-17
OK, thanks for your input. Please post more info later if you have any success in reducing the fan noise. I'm currently thinking of upgrading to the latest Ubuntu, but I won't if there's no improvement in this matter.

---

### Post by scrooge_74 on 2007-08-17
I think in the mean time we could all use either earplugs or headsets and listen to music :)

---

### Post by dj Kalma on 2007-08-19
Hey, my machine bent to my will and got a little quieter. Check out the whole story in [this other thread]("http://ubuntuforums.org/showpost.php?p=3216703&postcount=13") in which I accidentally posted.

---

### Post by shaft350x on 2007-10-14
I'd be interested to see if anyone has had anymore luck with this.  I've inherited my wife's old laptop (got her a Darter from System76), the laptop I have is this hp zv6000.  I have had some of the same issues with it running hot and the fan going all the time.  I did the cpufreq thing and scaled the processor down, but also could only ever get it to 1ghz.

My problem now is the fan is making a "grinding" sound.  It was intermittent at first but now it is constant.  Going to look into replacing it, anyone know where I could do that?

Also wondering if anyone has had anymore luck with Gutsy, I read that one of the new features is dynticks, that is supposed to do some of that scaling regardless of laptop or desktop.

---

### Post by scrooge_74 on 2007-10-14
I myself went radical and switch to Debian 4.1, which was a good choice for my nx6110, it runs with a lot less noise and is colde.  Besides I have less problems with suspend mode and with the wireless

---

### Post by CareyB on 2007-11-30
Problem, from my reading, seems to be that the maintainer of some of the ACPI stuff for Ubuntu decided that quiet was better, so locked the user out of changing the thermal trip points, like you used to be able to do.  Now that's just frickin' M$ish, isn't it?  If I want to listen to a fan, or fry my laptop, that's my choice, and the  Linux way ;-/

My Acer 3624 now runs with a constant CPU temp around 60C - THAT IS HOT!  It makes it uncomfortable to have it on my lap, impairs performance of the CPU, and my brick it at some point.

Come on, boys.  Back to the Linux way.

---

### Post by gerbazio on 2007-11-30
It seems to me the problem is related to other posts I've read around, included a post from myself:

[http://ubuntuforums.org/showthread.php?t=627482](http://ubuntuforums.org/showthread.php?t=627482)

[http://ubuntuforums.org/showthread.php?t=587443](http://ubuntuforums.org/showthread.php?t=587443)

[http://ubuntuforums.org/showthread.php?t=558765](http://ubuntuforums.org/showthread.php?t=558765) (this one is marked as "solved" but it is not true: the poster has simply accepted the absence of cpu-frequency-scaling, which had no consequences for him)

and maybe this one:
[http://ubuntuforums.org/showthread.php?t=627540](http://ubuntuforums.org/showthread.php?t=627540)

in all of them it is reported about cpu frequency problems appeared with the new ubuntu release, in particular note that: on ubuntu *there are* tools to manage frequency exactly like those in windows, for example the powernowd daemon, but actually in some cases it is not properly loaded in this new ubuntu version

---

### Post by rchar66 on 2007-11-30
I have a HP Pavilion laptop running Ubuntu 7.04 and it seems to be just fine at managing heat. The fan will only come on once in a while when I'm actually working on it. When it's sitting idle, the fan never even comes on.

---

### Post by CareyB on 2007-12-11
I think I've got it!!  Well...  some of it.  And now I have to **RTFM** myself :-/

Check this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

My Acer 3624 runs a Celeron M 1.6GHz (M for Mobile), but I used the P4 module, and set the governor to "ondemand".  It works fine.  Just put the CPU scaling applet in the task bar, and watch it change - woohoo!

Hard drive is warm, but I can look at some spin-down settings, now.

I still think the default trip points are stupid.

Look also at /etc/default/acpi-support

---

