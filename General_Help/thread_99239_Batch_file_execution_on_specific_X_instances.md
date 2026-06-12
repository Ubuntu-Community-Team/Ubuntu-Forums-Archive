---
title: "Batch file execution on specific X instances"
date: 2005-12-05
forum: General Help
---

### Post by nelposto on 2005-12-05
Hey guys.

What I'm trying to do is create a script that does some commands, and restarts the X window manager. After the X window manager loads I want it to execute another script, but not every time X loads... only when I run this batch file first.

For example batch1 in pseudo would look like:

command
command
restart x (onload open batch2)

Are there some command line arguments that I can pass while restarting X that will make it open a batch file after it has loaded? 

Thanks in advance

---

### Post by schdefan on 2005-12-05
What do you want to do with this script? 
Why do you want to restart X?
Do you change the configuration of /etc/X11/xorg.conf in your script?


schdefan

---

### Post by nelposto on 2005-12-05
[QUOTE=schdefan]
Do you change the configuration of /etc/X11/xorg.conf in your script?
[/QUOTE]

Yep.. what I want to do is overcome the fact that the fglrx drivers don't support hibernating.

So what I want to happen is: 
* edit xorg.conf to make the driver = ati
* restart x (save current setup)
* hibernate

The goal is that I can switch between operating systems withough always having to boot linux fully.

---

### Post by schdefan on 2005-12-05
When do you want to decibe if hibernate mode is enabled?
You can write different xorg.conf and load them as required at boot time with a script and put a link in /etc/rcX.d 
or do you want to switch after booting?
You can switch into runlevel1 with init 1 to avoid rebooting.

> The goal is that I can switch between operating systems withough always having to boot linux fully.
And for switching between different OS you don't need to reboot? 
schdefan

---

### Post by nelposto on 2005-12-05
I would just be using ubuntu normally. Then I decide that I need to go into Windows to do some work, or I need to leave to go somewhere and I'm taking the laptop with me.

I need for X to be using the ATI driver so that I can make the laptop hibernate. (If possible I would like it to all be automated - so the script changes the driver, restarts X and hibernates the computer)

This way when I reboot, the laptop doesn't load all of linux again, it only restores the old state.

---

### Post by schdefan on 2005-12-08
So, why don't you want to use the ati driver all the time? i don't get the point, sorry.
schdefan

---

