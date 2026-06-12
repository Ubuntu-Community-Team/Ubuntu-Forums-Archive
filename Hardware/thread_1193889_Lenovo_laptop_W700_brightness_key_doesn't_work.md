---
title: "Lenovo laptop W700 brightness key doesn't work"
date: 2009-06-22
forum: Hardware
---

### Post by zdmytriv on 2009-06-22
Lenovo laptop W700 brightness keys doesn't work. All the solution I tried on the internet doesn't work.


 Brightness 100% all the time.
 - Ubuntu Jaunty 9.04.
- Gnome
- $ uname -a
- Linux ******* 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
- Nvidia drivers 180.44
 I will provide additional information if needed.


 Thank you,
Zinovii


 PS: Mute key doesn't work either. But volume up and down control keys does.

---

### Post by zdmytriv on 2009-06-23
Anybody? 
My eyes are falling off :( Just too bright...

---

### Post by Luosto on 2009-07-31
I installed NVIDIA driver version 185.18.14 and now the brightness keys work.

---

### Post by mastertimothy on 2009-09-25
I have the exact same laptop and Ubuntu set-up as you.  None of the brightness controls work.  The buttons on the keyboard, the brightness controls in Ubuntu.  

When I use the brightness buttons on the keyboard Ubuntu responds.  It show the little notification thing.  The laptop just doesn't physically respond.

---

### Post by zdmytriv on 2009-09-25
I have solved this problem.
1. Install WindowsXP.
2. Boot into WindowsXP and set brightness.
3. Boot into Ubuntu and your brightness is set to the level you set in WindowsXP

Enjoy

---

### Post by nabinlimbu on 2010-01-17
Alternatively, you can go to Preferences -> Power Management. From here, you can change the brightness of your lenevo laptop.

---

### Post by zdmytriv on 2010-01-17
2 nabinlimbu: It doesn't work. 
Actually brightness keys change brightness value but not brightness of the screen.

---

### Post by gradinaruvasile on 2010-01-17
Have you tried pressing ctrl+alt+f1 and setting the brightness that way?(Then ctrl+alt+f7 to go back to the graphical interface)
Just a suggestion that probably wont work... 

I use this method on a Dell C640 with Ubuntu 8.10 but its old hardware with Ati card.

---

### Post by zdmytriv on 2010-01-17
2 gradinaruvasile: 
I doesn't work :(

ctrl+alt+f1 is actually another problem that I noticed with Lenovo W700. I can't see command like. Screen is just blank black and nothing going on.

---

### Post by gradinaruvasile on 2010-01-17
Ok.
Maybe try with booting in recovery mode... select root prompt, try to set the brightness, then ctrl-d and select resume boot.

---

### Post by zdmytriv on 2010-01-17
I solved it by rebooting to Windows, setting brightness there and reboot again to Ubuntu.
I'm not changing brightness often so it works for me so far this way.

---

### Post by VitalBodies on 2010-03-07
Try Fn END. 
Meaning the function key and then the End key. 
Fn Home for brighter. 
You might also figure out if you have an old bios...

---

### Post by zdmytriv on 2010-03-11
I've tried Fn key. Still doesn't work.

Don't know about bios. I'll check. Thanks


> **VitalBodies said:**
> Try Fn END. 
Meaning the function key and then the End key. 
Fn Home for brighter. 
You might also figure out if you have an old bios...

---

### Post by VitalBodies on 2010-03-11
Fn END and Fn HOME should work, if they do not you have to wonder why. 
Are you using the "Generic 105-key (intl pc) layout in System > Preference > Keyboard > Layout? 
And...
LAYOUT > US

---

### Post by zdmytriv on 2010-03-12
Ubuntu shows brightness indicator while I'm changing Fn-up/down but screen brightness doesn't follow to that indicator.
I'm assuming that sonething wrong with drivers screen drivers.


> **VitalBodies said:**
> Fn END and Fn HOME should work, if they do not you have to wonder why. 
Are you using the "Generic 105-key (intl pc) layout in System > Preference > Keyboard > Layout? 
And...
LAYOUT > US

---

### Post by VitalBodies on 2010-03-12
What are your power management settings for display? 
System > Preferences > Power management > On Ac Power
...and 
System > Preferences > Power management > On Battery Power

---

### Post by VitalBodies on 2010-03-12
This is off the subject of your issue, but did you get your W700 tablet, color calibrator or finger print reader going?

---

### Post by zdmytriv on 2010-03-12
Why do you think it has anything to do with brightness?



> **VitalBodies said:**
> What are your power management settings for display? 
System > Preferences > Power management > On Ac Power
...and 
System > Preferences > Power management > On Battery Power

---

### Post by VitalBodies on 2010-03-12
Since our brightness changes with the Fn END and HOME keys and yours does not, I thought it might help to match any setting that might be related. There is a slider for brightness in the power management settings - in some near or distant way it is related. Our brightness is set to 100% there.

---

### Post by zdmytriv on 2010-03-12
W700 is not a tablet.

I don't have finger print reader.

> **VitalBodies said:**
> This is off the subject of your issue, but did you get your W700 tablet, color calibrator or finger print reader going?

---

### Post by VitalBodies on 2010-03-12
My last suggestions are, bios settings, Bios version, video driver, video driver settings and what server your updates come from - ours come from the MAIN SERVER. 

Just trying to help...

---

### Post by zdmytriv on 2010-03-12
My doesn't react to brightness change in this preferences. The same brightness from 0 to 100%.



> **VitalBodies said:**
> Since our brightness changes with the Fn END and HOME keys and yours does not, I thought it might help to match any setting that might be related. There is a slider for brightness in the power management settings - in some near or distant way it is related. Our brightness is set to 100% there.

---

### Post by VitalBodies on 2010-03-12
> **zdmytriv said:**
> W700 is not a tablet.

I don't have finger print reader.

I know, it is high end mobile workstation and some have a digitizer built into the keyboard like ours does.

---

### Post by VitalBodies on 2010-03-12
**These setting work for us: (they might not all apply) **
**Nvidia:** 185.18.36 is the Nvidia driver version we are using and everything is at the defaults. 
64-bit: We are using 64 bit desktop Ubuntu are you? 
Updates come from: Main Server

---

### Post by zdmytriv on 2010-03-12
Did you install fresh Karmic Koala or you upgraded from Jaunty?

Might be that is the problem because I upgraded from Jaunty. 
It didn't work on Jaunty, might be it was fixed for Koala but didn't get upgraded...

Appreciate your help.


> **VitalBodies said:**
> I know, it is high end mobile workstation and some have a digitizer built into the keyboard like ours does.

---

### Post by zdmytriv on 2010-03-12
I'm using 173.14.20 and 32bit Ubuntu.

I'll try to install 185 driver...


> **VitalBodies said:**
> 185.18.36 is the Nvidia driver version we are using. 
We are using 64 bit desktop Ubuntu are you?

---

### Post by VitalBodies on 2010-03-12
Fresh install of Karmic not an upgrade. 
In fact we took the windows hard drive out to set it a side for when we resell the notebook someday - so it will be untouched un-used - and we put a new drive in and installed Ubuntu and told it to use the whole drive. 
Check my earlier posts from tonight (within this thread) to make sure you did not miss any.

---

### Post by VitalBodies on 2010-03-12
Our Nvidia driver is set to the defaults, meaning however Ubuntu loaded it - we did not change any settings. 
If you are pondering a clean install you might try the live cd for the 64-bit version since you have a workstation.

---

### Post by VitalBodies on 2010-03-12
If you fix this issue be sure to update this post and say what you think did it.

---

### Post by zdmytriv on 2010-03-12
NVIDIA driver installation failed for some reason. Something went wrong with my OS.

I'm going to give up for now. I will reinstall system for Lucid Lynx in a month and will reply if problem is gone.

Thanks.

---

### Post by VitalBodies on 2010-03-12
We made no bios changes from factory install. 
Ubuntu: 9.10
Kernel Linux 2.6.31-20-generic
Gnome 2.28.1

---

### Post by xjohnthomasx on 2010-03-28
BUMP.. same problem on lenovo u550.. did you solve? how? suggestions? also, filed bug report.. but no help/cure yet..

---

### Post by zdmytriv on 2010-05-08
After installing new Ubuntu (10.04) problem disappeared. Brightness and sound works fine.

---

