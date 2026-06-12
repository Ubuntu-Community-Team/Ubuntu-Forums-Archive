---
title: "Ubuntu 12.04 - performence issues with 2 external monitors"
date: 2014-04-06
forum: Hardware
---

### Post by asili22 on 2014-04-06
Hi

I have Dell E6400 with 2 external monitors - 1 connected via Display Port and 1 connected via VGA.
I have integrated I[COLOR=#333333][FONT=Arial]ntel[/FONT][/COLOR][COLOR=#333333][FONT=Arial]®[/FONT][/COLOR][COLOR=#333333][FONT=Arial] Graphics Media Accelerator 4500MHD[/FONT][/COLOR] graphics and I've noticed poor performance when the second monitor was hooked up.

Is this a known issue?
Is it possible to download latest Intel drivers that may solve my problem?

Asi

---

### Post by Double.J on 2014-04-06
Hi there! 

Just to check, with the externals connected, are you also running the laptop screen? I only ask because it looks as though this machine can officially support 2 displays at a time. Sometimes ubuntu will let you get around such limitations, but at the inevitable cost to performance.

Also how's you RAM usage? The gma4500mhd doesn't possess it's own video RAM, so takes from the system RAM - if you are getting low on RAM or swapping, performance will take a hit. 

It may also be worth looking in system monitor or using htop to check overall system load at the time. Does this happen instantly after booting with the two monitors running, or as more programs are opened?

also do you still have a dual boot to test if the same performance lag is occuring in windows?

You can also try loging out, clicking on the cog, and signing in with 'Ubuntu 2D' display selected.

for drivers, checkout answer 2 [here]("http://askubuntu.com/questions/338483/how-do-i-install-intel-integrated-graphics-controller")

---

### Post by asili22 on 2014-04-06
> **gnu/mirow said:**
> Hi there! 

Just to check, with the externals connected, are you also running the laptop screen? I only ask because it looks as though this machine can officially support 2 displays at a time. Sometimes ubuntu will let you get around such limitations, but at the inevitable cost to performance.

Also how's you RAM usage? The gma4500mhd doesn't possess it's own video RAM, so takes from the system RAM - if you are getting low on RAM or swapping, performance will take a hit. 

It may also be worth looking in system monitor or using htop to check overall system load at the time. Does this happen instantly after booting with the two monitors running, or as more programs are opened?

also do you still have a dual boot to test if the same performance lag is occuring in windows?

You can also try loging out, clicking on the cog, and signing in with 'Ubuntu 2D' display selected.

for drivers, checkout answer 2 [here]("http://askubuntu.com/questions/338483/how-do-i-install-intel-integrated-graphics-controller")

thanks for the reply.
I'm not running the laptop screen, only 2 external monitors are on.
RAM is ok, when I disconnect 1 screen everything works fine.
This is not happenidng in Win7 therefore I suspect that this is related to Ubuntu.

I will try to update drivers and then login with ubuntu 2d.
will keep you posted.

10x

---

