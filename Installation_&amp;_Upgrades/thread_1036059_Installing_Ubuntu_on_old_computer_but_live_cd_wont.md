---
title: "Installing Ubuntu on old computer but live cd wont work?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by Cellar_Sparkles on 2009-01-10
I just downloaded Ubuntu 8.10 and burned it to an cd and put it in the computer. THEN , what do you know more problems! I first clicked use Ubuntu without installing and then it when to the loading screen then it when to a blank black screen and nothing. I left it on for about 4 hours and nothing. So I went to install Ubuntu, same thing I get to the black screen and nothing. So I went to check disk for errors and it showed 11 errors. So I burned the cd again and the same thing happened and now it has error reading boot cd under the cd check. So idk why these things keep going wrong, any suggestions on how to get Ubuntu running on my computer, it an VERY old Compaq 5000us series and originally installed with windows ME.I have tried another time and same thing with 31 errors at a 6X speed. So idk what going wrong.

---

### Post by Partyboi2 on 2009-01-10
How much ram does the machine have? If its the default 64mb then you would be better of trying a lighter distro like [[COLOR=Blue]darn small linux[/COLOR]]("http://damnsmalllinux.org/") 
If you machine has 192mb or more of ram then you can try installing [[COLOR=Blue]xubuntu[/COLOR]]("http://www.xubuntu.org/get")

When you download the iso make sure that you check md5sums that they match before burning.

---

### Post by lykwydchykyn on 2009-01-10
It's possible the optical drive is bad, too.  IME old 98/ME/2000 era systems only have a working optical drive about 50% of the time.  You might want to try the alternate install CD, or install from USB if you can get the system to boot from USB.

---

### Post by Cellar_Sparkles on 2009-01-11
Well this is the problem I have, is I need an easy Linux to use as far as installing app.s and stuff. I did get dsl Linux to work correctly but i am a COMPLETE NOOB at Linux. I am using this machine for a MAME Arcade machine ( Multi-Arcade-Machine-Emulator, google "mame" for more info) and ubuntu seems like the only one that makes it easy to use for a complete Linux noob. Does anyone know of any other dist. that are easy like ubuntu? Or a fix to my problem?

---

### Post by Partyboi2 on 2009-01-11
> **Cellar_Sparkles said:**
> Well this is the problem I have, is I need an easy Linux to use as far as installing app.s and stuff. I did get dsl Linux to work correctly but i am a COMPLETE NOOB at Linux. I am using this machine for a MAME Arcade machine ( Multi-Arcade-Machine-Emulator, google "mame" for more info) and ubuntu seems like the only one that makes it easy to use for a complete Linux noob. Does anyone know of any other dist. that are easy like ubuntu? Or a fix to my problem?
You could try adding some more ram and using xubuntu which is is similar to Ubuntu, except that it has a different desktop. Or another one you could look at is [puppy linux]("http://www.puppylinux.org/wiki/hardware/general/minreq").

---

### Post by peterhb on 2009-01-11
> **Cellar_Sparkles said:**
> I just downloaded Ubuntu 8.10 and burned it to an cd and put it in the computer. THEN , what do you know more problems! I first clicked use Ubuntu without installing and then it when to the loading screen then it when to a blank black screen and nothing. I left it on for about 4 hours and nothing. So I went to install Ubuntu, same thing I get to the black screen and nothing. So I went to check disk for errors and it showed 11 errors. So I burned the cd again and the same thing happened and now it has error reading boot cd under the cd check. So idk why these things keep going wrong, any suggestions on how to get Ubuntu running on my computer, it an VERY old Compaq 5000us series and originally installed with windows ME.I have tried another time and same thing with 31 errors at a 6X speed. So idk what going wrong.

I've been fighting Ubuntu 8.10 (AMD 64) for some time now with similar problems to yourself. The ISO verifies against the MD5SUMs, verifies after burning, loads perfectly well as a live CD, but will not install, after reporting disk errors whilst copying files.

I've burnt CDs using several DVD/CD writers, several CD manufacturers and several imaging software products, including Nero and IMGBurn, under several operating systems. The obvious conclusion is that there is something flaky in the optical disk driver(s) in 8.10 as that is the only point of commonality.

However, I got there in the end by using a 3.5" DVD-RW as the recording medium and that is what this rambling preamble was all about. Maybe it will work for you? :)

Peter HB

---

### Post by snowpine on 2009-01-12
Hi there, here are the minimum hardware recommendations for Ubuntu: 

Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

Source: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

A better choice for your old hardware might be DSL, Puppy, or SliTaz. Good luck!

---

