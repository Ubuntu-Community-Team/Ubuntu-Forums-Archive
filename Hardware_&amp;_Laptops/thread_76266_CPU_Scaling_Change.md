---
title: "CPU Scaling Change"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by soulestream on 2005-10-14
I have a Dell 6000. After apt-get"ing" a few things everything works great.

Suspend even works

however my cpu scaling auto scales. I want to be able to adjust it manually from the little app in gnome-panel, like I could in Slackware. 

What do I need to change to allow this..

soule

---

### Post by bryan986 on 2005-10-15
Why do you need this? The CPU automatically increases it speed when there is more demand for it....

---

### Post by soulestream on 2005-10-15
1. Because its auto mode doesnt work well. It is useful when on battery, but I see no need to run my PentiumM 1.5 ghz at 600mhz all the time. 

2. It also makes opening windows and often compiling slower because it stays at 600mhz.

3. Its linux. If I wanted my system to tell me how it wants to run, I would use windows.;) 

soule

---

### Post by Braini on 2005-10-16
Hi,

The applet looks if it can use /usr/bin/cpufreq-selector to change frequency or governor but you must be root to do this.

So if you set the SUID bit on this program (sudo chmod a+s /usr/bin/cpufreq-selector) you will see the options to change frequency or governor.

I guess it would be better to make the user member of a certain group which is allowed to make the change but at least it works.

CU,
Michael

---

### Post by kashms on 2005-10-16
how do you make the applet (I presume we are talking about "CPU Frequency Scaling Monitor" panel applet) use cpufreq-selector command? I don't see any options in preferences.

---

### Post by Braini on 2005-10-17
You don't have to setup anything, it just uses it by default.

---

### Post by bmichel on 2005-10-17
[QUOTE=soulestream]1. Because its auto mode doesnt work well. It is useful when on battery, but I see no need to run my PentiumM 1.5 ghz at 600mhz all the time. 

2. It also makes opening windows and often compiling slower because it stays at 600mhz.

3. Its linux. If I wanted my system to tell me how it wants to run, I would use windows.;) 

soule[/QUOTE]

It should have some change in the cpu freq selector app.

Until one week ago, my laptop reacted very well and freq was always well adapted to the load. 

Since freq stays at 600 MHz or 35% of my overall cpu freq and it increases only when the load is very heavy. 

As your machine,  my laptop gives the impression to be less powerful and it starts to be annoying when I run many apps.

---

### Post by kashms on 2005-10-17
Are we talking about manually changing the frequency by using the applet? Nothing happens when I click on it. I should have 8 frequencies to choose from.

Although, in a terminal i can write:

$ cpufreq-selector -f 1900000

to change the freq to 1.9 GHz.

---

### Post by bmichel on 2005-10-17
[QUOTE=kashms]Are we talking about manually changing the frequency by using the applet? Nothing happens when I click on it. I should have 8 frequencies to choose from.

Although, in a terminal i can write:

$ cpufreq-selector -f 1900000

to change the freq to 1.9 GHz.[/QUOTE]

First sudo chmod +s /usr/bin/cpufreq-selector to give you some root privileges on this applet

second click right button on the applet go to preferences and now you should see a freq selector button.

---

### Post by DaveA on 2005-10-19
Thanks guys ;) 
couldn't get the applet to show governors nor frequencies.

I have another question:

I have a Sempron 3000 and I'm running Breezy on my laptop, an Acer Aspire 3023. I'm using linux-k7. Whenever I change my governor to "ondemand" the CPU only uses two steps 1600 & 1800 instead of all three: 800, 1600, 1800.
"conservative" governor seems not to work correctly too: it just keeps current frequency no matter what.

What could I try to fix these problems?

---

### Post by razahel on 2006-04-16
I am using dapper drake I can change the frequency via the applet but how can I set the governor because userspace is not very powersaving.
I know that I can echo it at every system start to /sys/devices/system/cpu/...
but is there a nicer way ?

regards razahel

---

### Post by kpolice on 2006-07-23
I followed this link [http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/) and I can select the governor & frequency. I have a Pentium M (Dothan).

---

### Post by robinlennox on 2007-05-13
How do I enable the CPU Frequency Scaling Monitor applet in gnome!!!

I can't find a package!

It would be really good to have it next to the clock as Shuja does!

---

### Post by kaede on 2007-05-14
try to search from synaptic package manager. i'm currently using emifreq package.

---

### Post by sistoviejo on 2007-10-30
To add cpu frequency monitor to a panel:
- Right click on a free space on the panel.
- Click Add to panel...
- Find CPU Frequency Scaling Monitor
- Drag it to a free space in the panel

---

