---
title: "slower running computer"
date: 2008-07-30
forum: General Help
---

### Post by mosaleh on 2008-07-30
I recently started running ubuntu for the first time on my home computer(woohoo!), im not running anything impressive its only a 2.8 ghz celeron with 256mb ram, and it seems like that ubuntu runs slower on my computer then windows does, is this right? are there any settings or tricks that i can do to speed this up? Right now i have only run firefox and pigeon, im a network admin at a school district so i do know my stuff about computers but with OS's specifically only windows though, i installed ubuntu to start learning some more, i would appreciate any help.

---

### Post by overdrank on 2008-07-30
> **mosaleh said:**
> I recently started running ubuntu for the first time on my home computer(woohoo!), im not running anything impressive its only a 2.8 ghz celeron with 256mb ram, and it seems like that ubuntu runs slower on my computer then windows does, is this right? are there any settings or tricks that i can do to speed this up? Right now i have only run firefox and pigeon, im a network admin at a school district so i do know my stuff about computers but with OS's specifically only windows though, i installed ubuntu to start learning some more, i would appreciate any help.

Hi and welcome. You may would have been better to choose xubuntu with that low memory. But if ubuntu is working then you may can just add some memory and get things going better. :)

---

### Post by prshah on 2008-07-30
> **mosaleh said:**
> I recently started running ubuntu for the first time on my home computer
its only a 2.8 ghz celeron with 256mb ram, and it seems like that ubuntu runs slower on my computer then windows does, is this right?


We really need more information than this; unfortunately, there are a lot of possible reasons why ubuntu is slow. I'd suggest you start with the following:

1) Is ubuntu actually installed, or are you running it from the Live CD? Or Wubi?

2) Is your display card setup for optimum performance? Here's a quick checl: Open a terminal (Applications-Accessories-Terminal) then give the below command ```
glxinfo | grep -i direct
``` If you get "Yes", that's fine, if "No" then the problem is (partially) with the display; in this case, post back for more information.

3) Have you setup any swap? Open the terminal and give the command ```
swapon -s
``` If there is no output, you don't have (but really, really need) swap.

4) Are you running extra "visual effects"? It is enabled by default in 8.04, but with only 256Mb RAM (And probably a chunk of it going to display memory), you cannot enjoy it properly. Turn it off with System-Preferences-Appearences-Visual Effects-None.

These are starting points; the problem could well be any, all or none of these.

---

### Post by mosaleh on 2008-07-30
ok cool thanks, ill try it as soon as i get home, and oh i appologies its not 256 its 512 memory, ill try the few other things and see what i get and report with my results 

-thanks

---

### Post by mosaleh on 2008-07-30
i also installed it and running without the cd, when i start the computer it gives me 2 options for OS's i have the windows xp and ubuntu, is this the correct way to install it, 

all i did was download the files, burn the cd and i ran the cd and insstalled ubuntu, is there another way to install it so that it is faster? or did i do it correctly?

---

### Post by jocko on 2008-07-30
> **mosaleh said:**
> i also installed it and running without the cd, when i start the computer it gives me 2 options for OS's i have the windows xp and ubuntu, is this the correct way to install it, 

all i did was download the files, burn the cd and i ran the cd and insstalled ubuntu, is there another way to install it so that it is faster? or did i do it correctly?

From your description, you did it the right way (if "ran the cd" means you booted the computer from the cd...).

With 512 Mb ram I think ubuntu should perform better than windows xp, at least my 1.86 GHz athlon processor ran windows quite poorly but runs ubuntu smoothly with 512 Mb RAM. A *fresh* install of windows (before installing antivirus and firewall) ran as good as ubuntu, but after installing antivirus and firewall, windows slowed down pretty much. Part of the slow-down in windows was solved when I increased the amount of RAM, but I guess the rest would require a processor upgrade.

When you say it runs slowly, do you mean that *everything* is slow, or just the graphics?
When you move a window, does it move slowly / disappear temporarily / move stepwise? In that case you are probably not using the best graphics card drivers.

---

### Post by prshah on 2008-07-30
> **mosaleh said:**
> i also installed it and running without the cd, when i start the computer it gives me 2 options for OS's i have the windows xp and ubuntu, is this the correct way to install it, 


Looks to me that you're using wubi; if you'd installed it by booting off it, you'd have atleast 4 options. Did you install ubuntu from within Windows, or did you boot off the CD, get a menu with option to choose language, and then another option to "Try Ubuntu without any change to your computer"?

With wubi, ubuntu will run slightly slower than normal; it should not be very noticeable. 

I think you can drop the first option and move on to the rest.

---

### Post by mosaleh on 2008-07-30
yea i installed it off of windows not from running off the boot disk

---

### Post by gazotem on 2008-07-30
Sounds like wubi

---

### Post by gazotem on 2008-07-30
Sounds like wubi.

---

