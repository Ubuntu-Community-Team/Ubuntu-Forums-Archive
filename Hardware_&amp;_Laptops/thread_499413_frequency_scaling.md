---
title: "frequency scaling"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by acrobat on 2007-07-12
hi all,
i have a asus f3jp with a intel t7200, and my processor is always at 2.0ghz .. it is not using frequency scaling..
is there any way to fix this? i'm running ubuntu feisty..

---

### Post by EXCiD3 on 2007-07-12
I dont know how to do it in GNOME, but on KDE the power manager can set your processor to dynamic. I set my HP dv9000t laptop to run at 1.0 GHz on battery and 1.83 GHz (max speed) when its on AC power. This app just sits in the tray on KDE, but I know there is a file somewhere that you can change this...i just dont know where its at...

I would also like to change mine because I switched back to GNOME and want to have the same frequency scaling in GNOME as i did with KDE.

---

### Post by acrobat on 2007-07-13
yes.. but in gnome i don't find any solution...

---

### Post by snap on 2007-07-13
if you have cpufreq-applet installed (it is by default in a standard ubuntu install with ubuntu-desktop) then just right-click on a panel -> add to panel, and then choose to add the cpu freequency applet.

now you will only be able to see the current freequency of the cpu in the applet.

now in a terminal try this 

```
sudo cpufreq-applet -g powersave
```

this should get your cpu to run at it's minimum

i use 
```
sudo cpufreq-applet -g conservative
```

if you setuid on the applet, you should be able to control the cpu mode from the gui applet itself.

do
```
sudo chmod 6744 cpufreq-applet
```
and now you should be able to do it from the gui applet, left-click on the applet icon in the panel and you should get a dropdown with the options.

Note: the modes powersave, conservative may not work for your cpu, they work for mine, i have a Pentium M 1.8Ghz

---

### Post by burito on 2007-09-01
I too have an F3JP, and the problem is, while the linux kernel does indeed recognize that the CPU supports freq scaling, cpufreqd and the cpufrequtils package appears to be too old to recognize this. Fortunately the problem is fixed in Gutsy, but that still leaves us Feisty users with a problem.

I suspect this is a Core 2 Duo thing, not sure as it seems the majority of people, including myself, are in the dark as to the specifics of the cores. And I fear Intel likes it that way.

---

### Post by burito on 2007-09-01
Ooop, silly me, a quick search for the term "f3jp" revealed this thread....

[http://ubuntuforums.org/showthread.php?t=448561&highlight=f3jp](http://ubuntuforums.org/showthread.php?t=448561&highlight=f3jp)

Which solves the problem perfectly.

---

