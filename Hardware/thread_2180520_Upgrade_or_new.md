---
title: "Upgrade or new ?"
date: 2013-10-13
forum: Hardware
---

### Post by pete of ebor on 2013-10-13
I've been running both Win XP & Ubuntu 12.04LTS on a dual boot setup (2 separate HDs). System is about 8 years old and has an  Intel® Pentium(R) 4 CPU 3.00GHz dual core with 2 Gb RAM and a Nvida GeForce FX5500 graphics card. This card is now too old to support anything newer than Ubuntu 12.04 - I've tried both 12.10 and 13.04 but the graphics response is almost unusably slow. I've also read that MS are stopping support for WinXP in April 2014, so I'll need to upgrade Windows as well as I need it for work related things. I understand that Win 8 probably won't work on this set-up, so the real question is  - is it worth getting a new graphics card or will I have to get a whole new PC ?

---

### Post by andrew732 on 2013-10-13
I myself want to use my XP/Ubuntu dual boot system for many years to come.  It's obviously a losing battle though.  I would say unless you can get an adequate graphics upgrade for very cheap (well under $100), it's probably time to do a system overhaul.  Good luck with that.  This new age of tablet-style operating systems without menus is very frightening to me.

---

### Post by mörgæs on 2013-10-13
The Pentium 4 series is single-core. 
Before ditching the old hardware I recommend a fresh install of Lubuntu 13.10. The FX5500 works fine when given a light desktop environment.

---

### Post by Topsiho on 2013-10-21
I agree with mörgæs.

I installed Ubuntu 13.10 on a computer with an AGP FX5500 graphics card, and it ran awfully slow. Processor busy 90% to 100% all the time with compiz and Xorg, even on the computer not doing anything (idle).

Installed xubuntu-desktop today, and on Xubuntu everything runs smoothly again. Processor is busy far less than 50% most of the time, when idle. Making the computer snappy again, and a pleasure to work with.

The processor is an Athlon 64 processor, single core.

The computetr ran 12.04 very well though, so maybe I'll return to that again, because I love Unity (without unwanted lenses).
And support lasts longer.

Topsiho

---

### Post by Yellow Pasque on 2013-10-21
Have you tried installing nvidia-173 driver?

---

### Post by Topsiho on 2013-10-21
Yes, thank you.

Topsiho

---

### Post by Topsiho on 2013-10-21
I have to complete my previous answer.

I installed the nvidia-173 driver while in Xubuntu.
I now find that booting into Ubuntu (13.10) gives me a screen which is magenta coloured all over, in which I can't do anything.

Leaving the computer alone for a while gives me a login screen, after entering my password I get that magenta screen again.
So the computer starts OK, but it is unusable in Ubuntu, using the nvidia driver.

It boots OK in Xubuntu, though.

Thanks for the hint, but tomorrow I'll install Ubuntu 12.04.3 back again on it. Worked like a charm for 1 1/2 years on this computer, but it is nice trying the new Ubuntu, which I now do since Warty Warthog :)

{ Warty was that good already that I fell like a brick for it, after trying RedHat (5.0 I think), Mandrake, Suse. These all came on 5 or more CD's, and after a number of updates, the files on the CD became obsolete, and so all dependency hell broke loose when updating next. Ubuntu was the first with very fast update servers distributed globally, and all necessary files in a repository, always up to date. Hell ==> Heaven :) Ubuntu could also handle a large number of updates at the same time, which the others could not (in 2004)}.

Topsiho

---

### Post by Johan De Cauwer on 2013-10-22
Never forget that 12.04 LTS is supported to mid 2017 - see [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) so there is really no reason to buy a new system, even when low-end systems are very reasonably priced. If it works...

---

### Post by Bucky Ball on 2013-10-22
DON'T install xubuntu-desktop in Ubuntu. If you want your 12.04 faster, install JUST the desktop environment, xfce4. Log out, check 'xfce4 session' from the sessions menu, log in. Feel the breeze. 

installing *buntu-desktop anything drags in a whole lot of stuff you don't need or want that will only bloat your machine, not streamline it.

---

### Post by Topsiho on 2013-10-22
@ Johan De Cauwer : Thanks for your info, don't worry however: this computer is the computer for experimenting. 
@ Bucky Ball: I think you are right. My Ubuntu install (13.10) was blasted by installing Xubuntu-desktop on top of it, AND installing the nvidia driver in Xubuntu. Probably I could configure nvidia in a terminal to solve thàt problem. Probably I will try that, and have to wait with installing 12.04.3 back again :)

My netbook (Acer one) runs splendidly with 13.10. With RAM extended to 1,5 GiB (from 0,5 GiB).
Xubuntu 13.10 has indeed a problem with the audio icon in the panel. Don't know where I read this ... but it is true.

Topsiho

---

### Post by mkmanifesto on 2013-10-23
> **mörgæs said:**
> The Pentium 4 series is single-core. 
Before ditching the old hardware I recommend a fresh install of Lubuntu 13.10. The FX5500 works fine when given a light desktop environment.

I assume he's referring to hyper threading when he mentioned dual core.

Like everyone else previously posted if you want to run a newer version of ubuntu your only option would be with a different desktop environment that doesn't require the additional juice.

Also just because Microsoft is going to stop supporting XP in April 2014 doesn't mean it will stop working. Your just going to stop receiving updates for it. Once April rolls around I would try to keep internet use on the XP side of things to a minimum.

Good luck!

---

