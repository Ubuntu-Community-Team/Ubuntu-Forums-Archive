---
title: "Has anyone installed any ubuntu variant on HP Pavilion dv6-2190us?"
date: 2010-04-08
forum: Hardware
---

### Post by Hetic on 2010-04-08
I am planning to buy an HP Pavilion dv6-2190us, if I can get a version of Linux on it. I was a bit discouraged by a newegg reviewer who said he could not do it, and by an email from an HP tech support saying they never tried Linux on it. However this forum seems a better place to ask this question.

Thanks

---

### Post by los-los on 2010-04-12
Hey dude,
 
I just bought that laptop and I'm planning to install ubuntu in a partition. It would be a waste having a quad-core and not having linux. Anyway i'm not sure if it will work well or not, i was thinking on wainting until the ubuntu people realeses the new version (10), but i will give a shot with the v9.1 and see what happen. I will keep you updated in case you want.
 
Cheers

---

### Post by akand074 on 2010-04-12
I don't see any reason at all why it would not work.

---

### Post by zampes on 2010-04-13
Hi there!
In my experience, HP laptops work well with ubuntu. I've had to install ubuntu and configure several pieces of hardware on at least 3 different HPs, two of which were dv4 1220us and the other a dv6, but an older one. The only trouble I've had with the 1220us was the microphone not working -somewhat solved by using directly kubuntu 9.10 KDE4.4... Other than that, there's usually nothing that can't be solved by asking around in the forums. I made a list of problems and given the solutions to them too... Try it out. One thing to remember is also that some people report problems with dual boot, because windows settings can alter the way your sound card work under linux -happened to me too. However, I'd stick to dual boot until you're totally comfortable with Linux to switch completely.

---

### Post by los-los on 2010-04-13
Hello Folks,

I tried to install a dual boot in my dv6 laptop, but i couldn't make it boot for the 2 systems (one at time, of course!). When i was able to use win7 i couldn't use ubuntu and when i could load ubuntu, win7 gave me a lot of errors. The other problem is that i only have this recovery discs that reset the laptop to the factory setup and it never gives me the chance to tell it which partition to use. could somebody give me some advises to get trough this? i really need linux and for other applications i need windows, so i need both.

Thanks

---

### Post by akand074 on 2010-04-20
> **los-los said:**
> Hello Folks,

I tried to install a dual boot in my dv6 laptop, but i couldn't make it boot for the 2 systems (one at time, of course!). When i was able to use win7 i couldn't use ubuntu and when i could load ubuntu, win7 gave me a lot of errors. The other problem is that i only have this recovery discs that reset the laptop to the factory setup and it never gives me the chance to tell it which partition to use. could somebody give me some advises to get trough this? i really need linux and for other applications i need windows, so i need both.

Thanks

Did you get this working yet? If not how did you install Ubuntu? I would recommend making a partition for Ubuntu in Windows and then manually installing Ubuntu using the live CD. Should work fine, I've done it many times and several computers I don't see how the Brand of the computer makes any difference at all they don't manufacture any of the internal parts and different HPs have different manufacturers of internal hardware and some are the same as other brands. The only problems I can see is the possibility of not having graphics drivers, but Ubuntu has support for pretty much everything to at least make it usable from what I've noticed for all recent hardware.

---

### Post by _0R10N on 2010-04-20
I have an HP 2170-us and karmic works fine, despite some issues that I'm still trying to solve:

- System freezes once in a while
- Sound keeps coming out from speakers when headphones are connected.

Kind regards!

_0R10N >>

---

### Post by Vaun on 2010-04-30
Running 64 bit 10.04 Lucid Lynx.  Everything works OOTB.  The sound issue with the headphone jack is still present.  The only _must_ upgrade is update the intel driver, if you have an intel graphics card, to v2.11.0.  The performance is much better as it's designed for these new GPU's.

---

### Post by ka1ser on 2010-05-12
I just installed Karmic on my dv6-2190us and everything is working like a charm... no freezes so far... 

Of course I had to do some things to get the most of it:

Downloaded and installed latest NVIDIA drivers.
Installed recommended Broadcom wireless driver. (System->Administration->Hardware Drivers).
In order to fix headphone jack detection issue, I tweaked /etc/modprobe.d/alsa-base.conf to use model hp-dv5 (adding a line in the end of the file: options snd-hda-intel model=hp-dv5 position_fix=0). Also I had to enable headphone jack detection option on alsamixer.

Another thing is that it just recognizes 3GB out of the 4GB of available RAM in 32-bit version. 64-bit version should show all the RAM. Also I think there is a tweak to get 36-bit address space to get the 4GB in 32-bit version but I haven't tried as I don't really need that 1 extra GB.

Hope this helps =).

---

### Post by NUboon2Age on 2010-06-08
A salesperson said that customers asked specifically for this machine because reportedly HP supplies Linux drivers for this machine.  Does anyone know about this?  My girlfriend is **considering one today(!) so if anyone has ANY insight on this, it would be appreciated.**

---

### Post by luigi_mb on 2010-06-08
I have installed Lucid on a dv7t. Everything works out of the box. I have not tested the tv tuner nor the microphone yet. Incidentally, does anybody have any experience with the tv tuner on this machine?

/luigi

---

### Post by dimsci_x on 2010-06-12
> **ka1ser said:**
> I just installed Karmic on my dv6-2190us and everything is working like a charm... no freezes so far... 


Every time i try to install it on my DV6-2190us it says "Filesystem check or mount failed"  and then goes to maintenance mode and I have the terminal and no gui? Did you have this problem?

---

