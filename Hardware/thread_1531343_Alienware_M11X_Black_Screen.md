---
title: "Alienware M11X Black Screen"
date: 2010-07-14
forum: Hardware
---

### Post by dragonmg on 2010-07-14
I have an Alienware M11X, R1. I want to dual-boot Windows 7 and Ubuntu 10.04.

I use the Wubi installer, and Lucid installs perfectly. I have uninstalled Dell Data Safe from the Windows 7 side, with no problems.

I boot into Lucid, and everything works fine. It finishes the setup with no problems. When I check the Hardware drivers, I have to install two drivers, one for the Nvidia Card, and one for the wireless card. Both drivers install with no problems.

I install all the software updates (230 of them), and everything is still running great.

I set up my programs exactly the way I want them: Chrome, GIMP, Open Office, etc... Still no issues.

So, after a bit of tweaking and surfing... I decide to shut off for the night.

When I reboot, I get the usual Boot Options: "Windows 7" or "Ubuntu"

I choose "Ubuntu". It makes me select a Kernel. I do so. And then.... Black Screen.

Any suggestions?

---

### Post by dragonmg on 2010-07-14
I think this has something to do with it:

[http://www.uluga.ubuntuforums.org/showpost.php?p=8898022&postcount=18](http://www.uluga.ubuntuforums.org/showpost.php?p=8898022&postcount=18)

> Ok, I have Ubuntu running on it. It looks like switchable = Intel and discrete = NVIDIA. If you try to install the nvidia closed source driver and it's set to switchable it will cause a kernel panic. If you install the driver when it's on discrete it will work fine, but then it will fail to start once you switch it back to switchable. (The graphics fail to work correctly on the splash screen and it didn't seem to get any farther. However, it didn't kernel panic on me..when I pressed the alien head it shut down.) 

That sounds like my symptom, but the OP didn't elaborate on how he fixed it.

Would anyone suggest NOT installing the Nvidia Drier? I don't really care about gaming for the Lucid side of the M11X.

---

### Post by dragonmg on 2010-07-15
I've isolated the problem to the Nvidia Driver. I purposefully did not install the driver, and have updated-rebooted-updated-rebooted several times, without incident.

Considering at some point I might WANT the Nvidia driver, does anyone have a suggestion?

---

### Post by Alfredo240 on 2010-08-03
I had the same Problem,

The solution is :
to install the Nvidia Drivers, in ubuntu, then restart the computer, enter the BIOS and Put Discreet Graphics  instead of switchable, which is the default.

PS when on battery remember it will eat the battery faster though.

---

### Post by Mecasickle on 2011-01-20
I also have an m11x with dual boot. Has anyone had any luck installing the nvidia driver on 10.04??

I'll be checking out the discreet graphics mode.

---

### Post by nutsy.ben on 2011-11-09
Same Problem here.

Also I'd like to use an external screen. 
Display and ubuntu were always a problem but this is the first time I struggle that much.

---

