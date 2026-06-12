---
title: "ATI Radeon refresh rates"
date: 2004-11-03
forum: Hardware &amp; Laptops
---

### Post by paul.hendrick on 2004-11-03
Hi all,
I'm running the latest ubuntu, with the fglrx-driver installed through synaptic.
i've setup my XF86Config-4 file using fglrxconfig, and chosen settings that I feel are correct, but no matter what i choose, i cant get a lower refresh rate than 85Hz. this is causing some bad static/artifacts on my screen, which usually runs at 75Hz with no problem.

i've even inserted a modeline, but that didnt work either. any other ideas? (i've attached my config file)

cheers,
paul.

---

### Post by paul.hendrick on 2004-11-03
i thought i attached the file...i'll try again :)

---

### Post by Magneto on 2004-11-03
[QUOTE=paul.hendrick]i thought i attached the file...i'll try again :)[/QUOTE]
what happens when you try the Screen Resolution application?

---

### Post by paul.hendrick on 2004-11-03
the only selectable rate is 85Hz, even when the config says the range is 60 - 75, for example. i'm completely stumped.
/var/log/XFree86.0.log file says that this file is being used, so i'm editing the right one, but it's having no effect.

---

### Post by Magneto on 2004-11-03
[QUOTE=paul.hendrick]the only selectable rate is 85Hz, even when the config says the range is 60 - 75, for example. i'm completely stumped.
/var/log/XFree86.0.log file says that this file is being used, so i'm editing the right one, but it's having no effect.[/QUOTE]

and you used fglrx config to generate that XF86Config?

---

### Post by paul.hendrick on 2004-11-04
Yeah, i used the fglrxconfig command to create the config file. 
cant figure this one out at all :(

---

### Post by Magneto on 2004-11-04
whats your monitor's make and model? are u sure about your hsync and vert refresh settings?

---

### Post by paul.hendrick on 2004-11-04
it's a Viewsonic G70fmb monitor. the setting i've chosen in Ubuntu are the same i've used in Fedora in the past, but with different results.

I've tried reinstalling the ati drivers, but that didnt have any effect either.

thanks,
paul.

---

### Post by tanari on 2004-11-04
i have the same problem 
radeon 32 sdr, viewsonic p95f+

---

### Post by Magneto on 2004-11-04
i think i know why it isnt working

your xf86config has 

# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 


try inserting this in XF86Config-4

# === Screen Management ===
#    Option "DesktopSetup"               "0x00000000"
    Option "MonitorLayout"              "NONE, CRT"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "30-70"
    Option "VRefresh2"                  "50-150"
#    Option "ScreenOverlap"              "0"

---

### Post by emperor on 2004-11-04
What model is the ATI card  that is being configured?
 
 The ATI fglrx driver is just for the 8500 cards and above. The older cards, like the 7500, 7200, 7000, 128pro, 128, and etc, use the standard XFree86 "ati" drivers.

---

### Post by Magneto on 2004-11-04
his card works with the driver, so it would have to be a supported card 
 read the thread

---

### Post by daniels on 2004-11-05
[QUOTE=emperor] The ATI fglrx driver is just for the 8500 cards and above. The older cards, like the 7500, 7200, 7000, 128pro, 128, and etc, use the standard XFree86 "ati" drivers.[/QUOTE]

No, fglrx is only for 9550 and above.  All r1xx and r2xx (every Radeon up to and including the 9250, going by model number) cards are perfectly well supported (including 3D) by the free driver.

---

### Post by paul.hendrick on 2004-11-05
My card is support by the fglrx driver, it's a Radeon 9200.

---

### Post by daniels on 2004-11-05
[QUOTE=paul.hendrick]My card is support by the fglrx driver, it's a Radeon 9200.[/QUOTE]
It will work perfectly fine with the standard driver -- if it doesn't, it's an easily-solvable bug.  fglrx is almost certainly not what you want.

---

### Post by Magneto on 2004-11-05
I was thinking this was a nonddc monitor issue - did you try that last suggestion?

---

### Post by wallijonn on 2004-11-05
Why not just tell it to use 75 - 75 when doing the config file?

---

### Post by paul.hendrick on 2004-11-08
Right, i'm still getting this problem. I've tried all the "solutions" proposed, but still i'm getting the weird articacts on the screen (they're not static spots, but flickering patches on the screen). are there any ideas? the only one i can think of is trying another distro, or moving to Xorg(which i've looked into and see it's not reccommended with ubuntu?).

any more ideas? (i've pretty much everything with fglrx, ati, radeon drivers).

cheers,
paul.

---

### Post by Magneto on 2004-11-09
[QUOTE=paul.hendrick]Right, i'm still getting this problem. I've tried all the "solutions" proposed, but still i'm getting the weird articacts on the screen (they're not static spots, but flickering patches on the screen). are there any ideas? the only one i can think of is trying another distro, or moving to Xorg(which i've looked into and see it's not reccommended with ubuntu?).

any more ideas? (i've pretty much everything with fglrx, ati, radeon drivers).

cheers,
paul.[/QUOTE]
use a different driver

try ati-gatos, try the ati driver from xfree86 4.3.0 - just the driver not all of x and switch all of X too if u want but u dont need to swap distros 
uninstalling one version of X and installing another is not rocket science

---

### Post by paul.hendrick on 2004-11-10
Yeah, i know switching X servers isn't hard, i've done it a few times, but after searching around I see people are having problems running Gnome + Xorg + Ubuntu, so I'm reluctant to do it.

I installed the X4.3 driver from ATi which i converted with Alien, restarted X and still no change.unloaded/reloaded the module, still no change. 
After a reboot though, I dont see the problem anymore.(fingers crossed)
I dont know why it's gone away, but I just hope it stays this way :)

---

### Post by Magneto on 2004-11-10
glad you had luck- i just switched from gentoo where i was using xfree 4.3 but my dual -head config wont work at all with ubuntu and i know its the version of the driver causing it - it sucks but its a small thing

---

