---
title: "temp. is rising :("
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by kanpachi on 2006-09-29
hello
i'm using an Amd athlon xp 2800 with 512 ram and 80gb wd hd
and i have dapper installed
recently i started getting hard freezes while encoding in avidemux or any other cpu consuming app
but it only happens once in awhile
so i decided to check my temp (i recently got a new case with a big fan on the back and a new cpu fan)
so i ran the gnome temp app and it showed 22 c
but i wanted to be sure, so i restarted my computer and checked the temp in my bios, and it said 67c!!!
so now i don't know what to do
i got 67c on my bios with my ac on and the computer is right below it, so something must be wrong?
i mean, if i was running my cpu at 67c, i wouldn't be able to do anything so it was const. freezing, isn't it?
could it be wrong? can the gnome applet be right?
if so, how come i still get hard freezes?

---

### Post by henriquemaia on 2006-09-29
Have you selected the right sensor in the applet? Maybe you're reading the motherboard sensor, for instance. Try with other sensors, if available.

---

### Post by joao82 on 2006-09-29
I have an athlon xp 2200+ and the cpu temp is around 45-50 degrees celsius when idle, and the most I've seen here is 55 degrees. But this is on windows. How can I see it on Ubuntu? I've installed gdesklets and went to the package manager to download everything that said sensors, but I still can't get any values for cpu temp. Am I missing something?

---

### Post by henriquemaia on 2006-09-29
Try checking out this thread:

[http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors+howto](http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors+howto)

It have worked for me on my Dapper.

---

### Post by tommcd on 2006-09-30
67 degrees is a bit high for idle, but is well within the max temp of 85C 

[http://www.cybercpu.net/howto/other/amdpr.asp](http://www.cybercpu.net/howto/other/amdpr.asp)

Perhaps try running the PC with the side door off, and place a fan (like a regular house fan) blowing in the PC and see if it helps. If it does then heat (and poor cooling) is likely the problem. Also, since you just got a new CPU fan, you could try reseating it. Use artic silver CPU paste, just a thin layer.
Also perhaps an additional case fan may help.

EDIT: also BIOS temp numbers are not always accurate.

---

