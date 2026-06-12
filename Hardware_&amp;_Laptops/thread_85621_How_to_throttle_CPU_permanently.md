---
title: "How to throttle CPU permanently?"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by anarchojens on 2005-11-03
Hello,

yesterday, I installed ubuntu 5.10 on my Acer Extensa 3000 Notebook, which has a Intel Pentium M 1.200 MHz. But on ubuntu, the clock seems to be dynamical, and, when many Programs are active, the CPU is at 1.600 MHz, which is too much. I had the Problem before under SuSE, but there I could throttle the CPU permanently to 50 %, and it ran at 600 MHz. Thats enough for me, because I do not play, and the slower, the more silent ;) I want that under ubuntu too, so, how can I do this. I`m totally new to it and did not find the right tool...

Greetings

Jens

---

### Post by grinias on 2005-11-03
Hi,

i do not know what you mean by "permanently" but if you do

```

sudo chmod +s /usr/bin/cpufreq-selector

```

and then you load the gnome-battery-applet onto your panel, you can change frequency scaling by left clicking that applet,  until your next boot :)

See you

---

### Post by anarchojens on 2005-11-04
First, thank you for your Help, this really changed behavior. Setting Frequencys simply doesnt change anything, but the "regulators" work (I hope, thats the correct name in English, I am using the German version). 
I am sorry for my bad english, but I am a little bit out of practice. With "permanently" I meant that when I boot up the system, CPU is at 600 MHz and it is on 600 MHz until I tell it to change Frequence. That is where I want to get, but your Help was a step in the right direction, so once again: Thanks :)

Greetings

Jens

---

### Post by grinias on 2005-11-04
You are welcome. It seems that we have the same goal but i haven't managed to do the permanent job either :)

See you

---

### Post by 23meg on 2005-11-04
[QUOTE=grinias]
and then you load the gnome-battery-applet onto your panel, you can change frequency scaling by left clicking that applet,  until your next boot :)

See you[/QUOTE]

I think that has to be the cpu frequency scaling applet rather than the battery applet. Also, if powernowd is running you'll have to kill it with the command ```
sudo killall powernowd
```.

---

### Post by iam10ninjas on 2005-11-04
If there are frequency/voltage settings in the BIOS, then maybe you can "hard wire" the CPU to run at 600MHz. In effect, you are underclocking the CPU to run slower. Using the BIOS to do it takes responsibilty away from the OS and is far more effective. 

This option has its drawbacks, as you have to be careful not to reduce your Front Side Buss speed too much, as this will hamper performance.

---

### Post by grinias on 2005-11-04
[QUOTE=23meg]I think that has to be the cpu frequency scaling applet rather than the battery applet [/QUOTE]

Yes, you re right. Sorry for that...

---

### Post by anarchojens on 2005-11-04
a friend of mine solved the problem obviously, meaning setting the mode during boot for whole session

needless to say that the cpufreq-applet for gnome has to be installed
since the cpufreq-selector skript ist included in this applet.

procedure for implementing :

1. copy/paste the following code in the file by 
    sudo vi /etc/init.d/setpowersave

```

#!/bin/sh -e
#
#   /etc/init.d/setpowersave: Set powernow mode to powersave, cpufreq-applet for
#                             gnome required (cpufreq-selector skript included here)
#                             otherwise
#                             cpufreq-selector skript at least needed
#
#			      setpowersave makes simple usage of cpufreq-selector
#				the same way cpufreq-applet does
#
#			      2005 alexander uhde, germany
#
# This configuration method is deprecated, please use /etc/network/interfaces.
. /lib/lsb/init-functions

log_begin_msg "Setting Powernow Mode to Powersave"
cpufreq-selector -g powersave
log_end_msg $?

exit 0

```

2. exit vi and sudo chmod 0755 setpowersave
3. sudo chmod +x setpowersave to make the skript executable
4. make symlink in runlevel 2 with: sudo ln -s /etc/init.d/setpowersave /etc/rc2.d/S99setpowersave
5. reboot -> powersave will be now set during boot, you can certainly set other modes still by using the applet

greetings

anarchojens + alex

---

### Post by grinias on 2005-11-07
Very good solution. Although in kde -which i use right now- everything is set as you wish by the respective kde cpu-frequency-scaling applet of them, since kde  "remembers" the scaling of your last session each time you login again.

Thanx anyway

Elias

---

