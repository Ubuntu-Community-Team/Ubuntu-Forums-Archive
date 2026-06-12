---
title: "ATI drivers (restricted)"
date: 2008-06-25
forum: Hardware
---

### Post by tmh177 on 2008-06-25
I have installed ATI drivers (restricted) and on re-boot, all I get is blank screen and I have to shut power of, then on again and as a result of this action I get corruption of Ubuntu OS.

I am leary now of trying the EnvyNG driver install, as I might get same results, any suggestions?


TMH177

---

### Post by MasterSander on 2008-06-25
Doesn't matter if you screw it up, you can always reinstall and it's better to have it fixed. You can always log into terminal by pressing ctrl+alt+f<1-6> and get back with alt+f7, then you can use apt-get install EnvyNG and uninstall the other driver

---

### Post by stchman on 2008-06-25
> **tmh177 said:**
> I have installed ATI drivers (restricted) and on re-boot, all I get is blank screen and I have to shut power of, then on again and as a result of this action I get corruption of Ubuntu OS.

I am leary now of trying the EnvyNG driver install, as I might get same results, any suggestions?


TMH177

Did you try enabling the ATI restricted driver?

---

### Post by tmh177 on 2008-06-25
> **MasterSander said:**
> Doesn't matter if you screw it up, you can always reinstall and it's better to have it fixed. You can always log into terminal by pressing ctrl+alt+f<1-6> and get back with alt+f7, then you can use apt-get install EnvyNG and uninstall the other driver
**When I enabled the restricted ATI driver and apply**, Ubuntu asks for re-boot, which I do, I then get the dual boot screen (Vista/Ubuntu)on 
re-boot.

I then enter Ubuntu as choice and it starts to lunch ,as far as the bars go across, then all goes blank on monitor, so I have no idea what is on screen as nothing is visable, only thing it that screen is blank and monitor power button is yellow intead of green, so having blank screen I can not get to login or terminal.

As stated before only thing I can to is power of computer, then when I boot up again into Ubuntu , error messages come about unclean unmount, which it tries to fix, but it can not.

As a result I have to delete partion through LiveCD, then re-install, thsat is why I am leary of trying the other method.

Card I have is ATI Radeon X700 series. I just do not want to do another install if the EnvyNG driver install does same thing.

TMH177

---

### Post by sevenearths on 2008-07-05
I am having the same problem with a 'ATI Radion Xpress M200' (EnvyNG drivers). If anyones got any ideas (esp. logs I might be able to post here) its not a problem.

Though this is becoming a real problem! I'm having to boot one or twice into black screens (do 'fsck' to sort out the unclean shutdown) before even getting a log in screen. This is lame and doesn't make ubuntu fun to use any more :(

---

### Post by tmh177 on 2008-07-05
Finally got it to work last night, all is ok now. Do not know how I go it to work though?

Things I did last night in no particular order was completely remove the restricted hardware driver program, made sure all updates were applied, installed EnvyNG driver and ran that, then did ATIconfig --initial, even went into BIOS and changed AGP Aperture Size to the maximum figure allowed in BIOS.

One of these steps, allowed the driver to load without a black screen appearing. 

TMh177

---

