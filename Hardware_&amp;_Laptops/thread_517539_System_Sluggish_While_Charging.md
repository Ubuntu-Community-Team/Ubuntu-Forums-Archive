---
title: "System Sluggish While Charging"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by Max Luebbe on 2007-08-04
I have a Sony VGN-FS760/W laptop running 7.04

When the system is running purely on battery, I get full performance and everything runs great.
When I have the ac adapter connected, I experience a noticeable performance hit that can be seen in lag when typing at a terminal or when it goes to to my GL based screensaver, a lag every few frames. This laptop is about a year old (1.86 centrino/geforce 6series mobile) but there's no reason it should be getting worse performance than my ancient 2400+/440mx desktop machine!

I am looking either for a solution, or a method to start further investigating. Any suggestions would be appreciated in helping me track down what's responsible!

---

### Post by Max Luebbe on 2007-08-06
No ideas even where to begin on this one?
Profiling Tools? Anything?

---

### Post by bbbscarter on 2007-08-09
Yup, I'm getting the same thing - well spotted, I've been trying to work out for ages what was causing it!

Sony S4XP, Feisty, running latest nvidia drivers (100.something). 

Hold down a key in a terminal - with AC attached it's sluggish and variable, on batteries it's fast and consistent.

Not sure if it has anything to do with hibernation.

---

### Post by SomeGuy on 2007-08-10
i too have this issue with my sony vaio
i can only watch about an hour of video before my battery needs charging... then the frame rate drops to an unacceptable level

the easist way to test this is as bbbscarter says, hold down a key in a terminal see it lag then pull out the power cable

its worth noting here that if i run glxgears while power is in everything goes fast again!

i believe this may have something to do with cpu scaling with my intel centrino cpu, but i am confused
i had a look at
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

i tried manually setting my power scheme to all differenet values to no avail
i also tried rmmoding speedstep-centrino

its doing something weierd where unless cpu is max it doenst want to put in any work even tho cpu freq is 100%

---

### Post by SomeGuy on 2007-08-11
my current really really dodgy solution (emphisis on bad solution)
is to run say
nice -n 19 glxgears
while watching video, which causes it to throttle cpu or wat ever is affecting **** into full speed
the command btw just says
run glxgears with lowest priority

---

### Post by Max Luebbe on 2007-08-15
So it isn't just me!

We need to do some more research on this.
I am a coder and am not afraid to get my hands dirty and waste some of my life working on a patch, I just need to know where to begin.

What kernels are you all using?
I had heard with an upcoming version, that the sony support was being entirely redone.
Anyone know more about that?

---

### Post by Max Luebbe on 2007-08-16
My cpu scaling does work, so we can rule that out.

Has anyone filed a bug report?

---

### Post by bbbscarter on 2007-08-16
Kernel version is 2.6.20-16-generic

CPU scaling is working for me too, although it's always on demand on batteries and on full when on AC - not sure how to make it go on demand when on AC as well, which might be worth trying in case the CPU scaling mode is related to the bug.

I haven't filed a bug report yet. 

Let us know how you get on!

Simon.

---

### Post by Max Luebbe on 2007-08-17
Hm.

Are you using the scaler applet in Gnome?
If so, in order to be able to command a particular frequency you need to run the following command:
```
sudo chmod +s /usr/bin/cpufreq-selector
```

Because in order to change the cpu frequency, the program needs to run with root permissions.

Let me know if you've done this, because this may help in ruling out the cpu scaler as the cause.

---

### Post by bbbscarter on 2007-08-17
Ah, cool, I didn't know about that. I can confirm then that the cpu frequency isn't the issue - if I change the cpu frequency so it's consistent when on and off AC, the problem still only occurs when on AC.

As an aside, the system monitor tells an interesting story. On batteries, cpu use when idle is generally around 2% with small spikes at 20%, mostly caused by system monitor itself. On AC, this rockets up to a consistent 70-80%, again with system monitor making up the bulk of the reading. Very odd.

Hope this is helpful...

---

### Post by Spartan.II.117 on 2007-08-17
Suggestion: check in your biso to see if there is any kind of profiles option there, also check your cpu speed in both modes, see if it changes.

---

### Post by Max Luebbe on 2007-08-19
I had just noticed the same thing - I think its time to file a bug report.

---

### Post by Max Luebbe on 2007-08-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/133533](https://bugs.launchpad.net/ubuntu/+bug/133533) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bug filed, please chime in with your own observations.

[https://bugs.launchpad.net/ubuntu/+bug/133533](https://bugs.launchpad.net/ubuntu/+bug/133533)

---

### Post by Max Luebbe on 2007-08-24
Switching from the generic kernel to the 386 kernel eliminates this issue.
The bug is related to a problem with centrino support in the generic kernel.

---

### Post by bbbscarter on 2007-08-24
Excellent stuff - thanks for the update.

---

### Post by bbbscarter on 2007-09-25
It also seems this is fixed in Gutsy, without having to install the 386 kernel.

Remarkably, hibernate/resume also seems to work properly, without any tinkering, and with the binary drivers. Hurrah!

Simon.

---

