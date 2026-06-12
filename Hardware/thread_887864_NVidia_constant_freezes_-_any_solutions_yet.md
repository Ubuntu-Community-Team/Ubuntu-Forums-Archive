---
title: "NVidia constant freezes - any solutions yet?"
date: 2008-08-12
forum: Hardware
---

### Post by !ndy on 2008-08-12
Hi there, 

I have spent at least 8 hours until now, trying to ix constant freezes on my computer.
I have just read hundreds of posts from people complaining or suggesting some placebo-style medicine. 

Is there anything, that can help with those system lockups or is it true, that I have just two (and a half) options:

1. use ubuntu hardy without restricted nvidia drivers
2. use ubuntu feisty - i have heard, that its pretty much okay with nvidia
3. use another OS

some info:
monty@Perfect:~$ uname -a
Linux Perfect 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
monty@Perfect:~$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)

I am running hardy version 8.04.1
and drivers from EnvyNG (version 173.14.12)

I cannot even play SuperTux2, as it freezes after 1 minute? Two times i tried it - it was the same.

And the last question:
i have read somewhere, that even if the system is completely frozen, using alt+sysrq and typing reisub can help. what is that :-)?

thank you for any help

---

### Post by starcannon on 2008-08-12
I've never installed on a GO 6100 before, but I have done so on many other models, including some old 5xxx series, and I personally own and use a 6600gt.

That said, try my guide, its how I do all of my nvidia installs, and I've done a bundle of them.

Follow the link below to look at my guide (don't skip steps).

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by nicedude on 2008-08-13
I love my Nvidia with Hardy, works like a champ with no freezes glitches or anything else. But then again I get the latest Nvidia driver package from Nvidia and install it myself, which both isn't hard and will teach you allot about your system ( like how to start and stop X and how to use the other ctl+alt+Function keys )


You could also try envy-ng if you want a program to try and do it for you.


Good luck and happy Ubuntu-ing

---

