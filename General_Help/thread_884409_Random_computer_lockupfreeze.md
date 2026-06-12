---
title: "Random computer lockup/freeze"
date: 2008-08-09
forum: General Help
---

### Post by zozoman on 2008-08-09
Hello everyone, I installed Ubuntu two days ago and so far I've been in the process of getting old programs and games back. Let me give a little background information on my computer spec and setup.

I have:
AMD Opteron 148 processor @ 2.8ghz
3 gigs of ram
GeForce 7800 GT
2 widescreen monitors (I am using twinview with the newest nvidia drivers with apt-get)

Ubuntu 8.04 64-bit
Wine
World of Warcraft - Using Wine
Azureous
Ventrilo - Using Wine

I have seen my computer lockup with Compiz on and with it off. I generally encounter lockups with Ventrilo and azerous open, but they are always open so I can't put 100% blame on them.

I don't know if I can post some log that would say what error happened.

So, any help would be appreciated into solving these random lockups!

-Alonzo

---

### Post by mikjp on 2008-08-09
In my experience, random freezes are usually caused by problems with graphics card. 

You could try to use your computer some time with another window manager (openbox) or desktop environment (KDE) to see, if the problem is in the way GNOME uses your video card. Sometimes I have just changed the distro when having problems like that, I don't want to spend days for locating problems with xorg if some other distro runs fine.

Does the problem persist, if you disable the twinview and use only one screen?

greetings,

mikko

---

### Post by Kain000 on 2008-08-09
Are you running stock clocks or is your rig overclocked?  I've noticed after switching form windows on my benchmarking rig that was running a heavy oc that ubuntu, and espacially firefox (because it's a memory hog!) were crashing my system. Most likely because the mem was clocked to high.     So i've reduced my clocks to stock and the system is WAY more reliable.  

so if you are overclocking your system be sure to either
           set it back to stock because it really doesnt seem to make ubuntu run faster
        or
           up your VDIMM (voltage to your DIMM or memory slots) and/or VCORE (voltage to your CPU. 
either of these could make your system more stable at higher frequencies.

if not you may want to increase the voltage to your memory or vid card BY VERY VERY SMALL INCREMENTS as to aviod dammage/overheating as more power can make components more stable.   However if your system is not overclocked I'd look into the post above mine before any voltage changes.

hope this helps

---

### Post by zozoman on 2008-08-09
I just got a another crash again...

To Kain000:

This computer is about 5 years old and when I did get it I did over clock it to 2.8 ghz.

I experienced this crash when I was in Compiz playing around with the Cube and moving windows around really fast, I'm not sure if that invoked it or if it was only a coincidence, 

I would like to not revert back to default speed, but if necessary I will.

To mikjp:

I did not disable TwinView yet but I am going to now.

---

### Post by Kain000 on 2008-08-09
I reciently had my E6420 core 2 duo from 2.1GHZ to 3.6GHZ for the forum wars oc comp.  and kept it arround 3.3GHZ for every day use and in windows it worked fine, however linux from what i've seen and read doesnt do well in an overclocked enviroment. I backed them back to stock and havent noticed any changes really (most likely because the oc was causing the system to hang all the time.)   However if you want to keep your clocks as is you will most likely need to up the voltage to make the enviroment more stable and that might help.  otherwise you should just back off the overclock just to see if that corrects the problem.  If not you have narrowed the problem down and havent really changed anything in your system.

---

