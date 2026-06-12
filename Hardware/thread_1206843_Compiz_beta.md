---
title: "Compiz beta?"
date: 2009-07-07
forum: Hardware
---

### Post by Gushter13 on 2009-07-07
Is there a BETA version of compiz?
I'm currently having random freezes when using any level of compiz effects on my system. I'm using the default version that comes with Ubuntu 9.04. My graphics card(s) is(are) NVidia 9100 + 9300 (Hybrid Power). I have no problems when i turn off Compiz!

Any help appreciated.;)

---

### Post by overdrank on 2009-07-07
> **Gushter13 said:**
> Is there a BETA version of compiz?
I'm currently having random freezes when using any level of compiz effects on my system. I'm using the default version that comes with Ubuntu 9.04. My graphics card(s) is(are) NVidia 9100 + 9300 (Hybrid Power). I have no problems when i turn off Compiz!

Any help appreciated.;)

What driver are you using? I have switched to the 185.xx nvidia driver.

---

### Post by shatterblast on 2009-07-07
My first suggestion includes updating your video drivers through "envyng-qt", which can be located in Synaptic.

Synaptic can be found by accessing:

System -> Administration -> Synaptic

Compiz has software "hooks" of a sort that access compatibilities with hardware drivers because of how it integrates.  While recent drivers may work well for gaming, a few operating system features may still require updated drivers since programmers invent new things to compete for attention somehow.  (And ultimately, the possibility of financial support.)

---

### Post by Gushter13 on 2009-07-09
> **overdrank said:**
> What driver are you using? I have switched to the 185.xx nvidia driver.

I'm using 180.xx.

---

### Post by Gushter13 on 2009-07-09
> **shatterblast said:**
> My first suggestion includes updating your video drivers through "envyng-qt", which can be located in Synaptic.

Synaptic can be found by accessing:

System -> Administration -> Synaptic

Compiz has software "hooks" of a sort that access compatibilities with hardware drivers because of how it integrates.  While recent drivers may work well for gaming, a few operating system features may still require updated drivers since programmers invent new things to compete for attention somehow.  (And ultimately, the possibility of financial support.)

Nope. Didn't fix it. It only made my system recover for a short while.

How do I update my nV driver?

---

### Post by shatterblast on 2009-07-09
Here is a risky link.  I have not tested it.

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Otherwise, there is a long way of doing it manually.  Guides exist that cover the process, and I care not to go into detail.

---

### Post by Gushter13 on 2009-07-11
Thanks, for the "heads up".

---

### Post by shatterblast on 2009-07-11
Also, you might access the nVidia driver updates from Synaptic by enabling "Pre-Released Updates" within the Software Sources windows.  That can be found under:

System -> Administration -> Software Sources -> the Updates tab at the top.

---

### Post by Gushter13 on 2009-07-17
Thanks

---

### Post by trelayne on 2009-07-21
Gushter13,

I've had the EXACT same problem for weeks since I installed 32-bit Jaunty on my Dell 
laptop Precision m4400 (nvidia Quadro FX 770m, 512MB). I've tried the following to no 
avail:

1. downgrading X a notch
2. installing the latest version of the nvidia driver (185.18.14)
3. installing the latest version of the nvidia driver (185.18.14) with a patch
    to fix refresh issues. Refresh works fine now---but freezes continue
4. upgrading the default Jaunty kernel (2.6.28-13) to the mainline 
    Ubuntu kernel 2.6.30-020630rc1-generic
5. messing around with /proc/mtrr settings -- as some have done successfully in 
    freebsd when encountering the same problem, on the same machine as mine
6. checking the following logs for anomalies during freezes--found nothing:  kern.log,  
     syslog   , messages,   Xorg.0.log, ~/.xsession-errors .  
7. trying the following to get compiz output to see what's happening during freezes:
    metacity --replace
    nohup compiz --replace

But none of these things have resulted in any new info or prevented the 
freezes from happening. They seem to start a few hours after boot time, then 
increase in frequency, each time forcing me to Ctrl-Alt-F1 to console, then Ctrl-Alt-F8 
to get back. For some reason, if I don't do that, it remains stuck in the freeze state for a
longer period of time.

Any insight from anyone greatly appreciated!

---

