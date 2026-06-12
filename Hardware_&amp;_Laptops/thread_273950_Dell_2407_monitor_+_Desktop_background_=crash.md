---
title: "Dell 2407 monitor + Desktop background =crash"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by imaca on 2006-10-09
I have recently got a 24" Dell 2407WFP monitor - it seemed to be running fine but if I have a desktop background when I log in it quits out of xwindows to log in screen repeatedly - it usually takes 4-5 login attempts to get desktop running.
Once going there are no problems. If I use CTRL ALT BACKSPACE there is an error message "glibc detected *** malloc(): memory corruption".
Is this a memory (hardware) problem or can it be fixed?

---

### Post by gonesolo on 2006-10-09
ok firstly it's unlikly to be your monitor. BUT in case I'm wrong try changing your monitor to a Plug n Play monitor and restart and see if that resolves it (in case the Dell monitor file is corrupt)

Otherwise a few q's if you will

1: does this happen in any other OS? do you have another OS installed? If not does it happen when you boot to the Live CD?

2: What video card have you got (card, mem, etc).

3: If you login with no desktop background and run a program (say frozen bubble or tux) does it work ok for you?

4: Does it happen with any background file? Have you tried downloading a new file and using it instead?

5: do you have another monitor you can try on the system?

to explain why for all these

1: if it does not happen in any other OS it's probably not hardware

2: so can check for driver issues etc

3: a game is more video intensive (generally) than you're standard desktop background, no issues in a game would usually again indicate a file/background image problem

4: leading on from above, if another background image works ok then it could be corrupt file. D/l a new file from the internet allows you to rule out any local corruption

5: to be sure it's not the monitor try another one

---

### Post by imaca on 2006-10-11
Have no problem with 3d games, or with winXP.
Also I wrongly assumed background image was the problem.
Even without wallpaper it still quits to login screen or locks up totally.
If I can actually log in it is totally fine.
In desperation I reinstalled ubuntu, formatting /root and /boot partitions (but not /home).
Interestingly install disk booted fine (it did NOT use 1920x1200 resolution).
After install problem is exactly the same!(even tho using ati rather than fglrx)
Perhaps problem is xorg.conf.
Can anyone tell me correct settings for monitor?

---

