---
title: "How do I know if my graphics driver is working correctly?"
date: 2009-06-08
forum: Hardware
---

### Post by Danbo19 on 2009-06-08
Hello all,
I just installed linux mint on my girlfriend's Dell inspiron 1525, it has an Intel Integrated Graphics Media Accelerator X3100 . Everything else in Linux Mint works fine, its fast, but I can't enable desktop effects. From what I understand about Linux Mint is that the driver should come as default. When I first installed Jaunty on my own laptop everything was really slow and jerky until I enabled desktop effects. Once I did that Ubuntu just searched for the necessary drivers and then everything Just Worked from then on. 
     But now on my girlfriend's laptop, in Linux Mint, which is supposed to come with all the necessary drivers I can't get the desktop effects (which are, in my opinion, some of the coolest things in ubuntu)  to work.
     I ran compiz check and got the following results:
rachel@rachel-laptop ~ $ ./compiz-check

Gathering information about your system...

 Distribution:          Linux Mint 
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


Does anybody have any idea what my problem is? Is it the graphics driver? Or is it some other problem? Thanks in advance.

---

### Post by keplerspeed on 2009-06-08
Jaunty had blacklisted the driver for this card, due to poor performance. Did you install the januty version of mint (7 i think)?

My girlfriend has a Dell inspiron 1525 too, but running an older version of mint (5) so that the graphics driver can be loaded, without any tinkering.

---

### Post by keplerspeed on 2009-06-08
here is a thread concerning the intel graphics [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by Danbo19 on 2009-06-08
Thanks a lot, I'll try doing that. I just switched to using Ubuntu about two months ago, so my command line experience ends at copying and pasting code I can find in these forums. So I'll be backing up her files before I try messing around with that.
     
So what graphics cards does Ubuntu like? I'm probably going to get a new laptop in a year. What graphics cards work really well? Or would it be better to go with a Dell laptop with Ubuntu already installed? Thanks again for the help.

Oh, and yes it is the Jaunty version of Mint, version 7. So, I'm pretty sure you're right about the problem.

---

### Post by Danbo19 on 2009-06-08
Okay, so I tried the guide you suggested, it seem to help in some areas like video playback, but I was still unable to turn on desktop effects. First I tried the safe version, then I moved on to the optimal. However, optimal disabled her wireless. 

I may just install mint 5 instead. If that version has the required drivers included, I might as well use it. Why would Ubuntu blacklist a driver just for poor performance? Without it you can't play games, enable desktop effects, or even screen savers. Any chance the driver will be included in 9.10? Thanks again for the help.

---

### Post by Danbo19 on 2009-06-24
[Solved]Re:Mark post as solved

---

