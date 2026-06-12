---
title: "karmic freeze before install"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by acracker on 2009-10-29
I burned the 64-bit desktop version of 9.10, loaded it in, selected English language, then selected the "Install Now" option. I get a cool white Ubuntu graphic pulsing for about a minute then the cd spins down, the graphic freezes and my computer hangs.

I tried the safe graphics option, tried booting into the live cd, same result. The graphic freezes its animation and my computer hangs. Caps/Num/Scroll lock keys are unresponsive.

I checked the cd for defects, it's fine. I ran the memtest program and got no errors. I had 64-bit 9.04 installed about a month ago, then I upgraded to Windows 7 (over ...uugh.. Vista) in anticipation of dual booting with W7 and Karmic. W7 runs fine so I know its not a hardware problem.

Anyone else have this issue and/or more information?

My hardware:
Intel C2Q 9550
ATI 4850X2
4GB ram, DDR2 800

---

### Post by Rocket2DMn on 2009-10-29
The LiveCD video support has gotten much better over the years, but sometimes it doesn't work.  If you can spare the bandwidth, I would just go ahead and skip straight to using the Alternate install cd rather than fiddling with the LiveCD.  You can get it from the [Ubuntu download page]("http://www.ubuntu.com/getubuntu/download") by clicking "Alternative download options, including Ubuntu installer for Windows" and select "Text-based installer".  This uses a pseudo-GUI which is actually very easy to use, so don't be intimidated.  The disc just doesn't have a Live session which you probably don't need since you are already just planning on installing.

---

### Post by acracker on 2009-10-29
Ok I'll try the alternate CD and post back when I get some results. Keeping my fingers crossed.

---

### Post by chanfle on 2009-10-29
eeyyy
please run first LiveCD...maybe detect any error when run boot process

---

### Post by chanfle on 2009-10-29
> **acracker said:**
> Ok I'll try the alternate CD and post back when I get some results. Keeping my fingers crossed.

I hope run alternate CD....because Karmic it's beautiful  :)

---

### Post by acracker on 2009-10-29
Ok, installed 9.10 via the alternate install CD, but I get the same problem when I try booting: the white Ubuntu graphic appears on the screen, but nothing else and then my computer hangs. My hard disk activity light comes in the beginning of the boot process, but soon turns off when my computer hangs.

I tried booting into the recovery mode and booting continues until it tries to start AppArmor profiles, then it hangs. Once again, no response from caps/scroll/num lock keys.

Here are the last two lines on my screen:
* Setting preliminary keymap...
* Starting AppArmor profiles

with a blinking underscore on the right side of my screen.

I used ext4 for the / and /home partitions and created an 8GB swap partition. Maybe I should try ext3?

---

### Post by Rocket2DMn on 2009-10-29
Are you able to get to a tty by doing CTRL+ALT+F1 and logging in to the command line interface?  If so, it would appear that something is wrong with X.

---

### Post by acracker on 2009-10-29
No, I press Ctrl+Alt+F1, but nothing happens. Still locked up at "Starting AppArmor profiles". I did this in recovery mode and in generic startup with the same result.

I originally thought that my problem was what these people were describing:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/444123](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/444123)

However, they mention being able to boot to the desktop and I'm a ways away from there. Their problem seems to be an Xorg issue like you mentioned.

Just for the heck of it, I'll try installing the 32-bit version of Karmic. Thanks for the suggestions so far Rocket, keep 'em coming!

I'll post back with results of the 32-bit trial.

---

### Post by RJARRRPCGP on 2009-10-29
LOL, sounds a lot like what happens when the video card is newer than the version of Ubuntu you have, like when I tried to use Dapper Drake with my GeForce 7600 GS and ended up with just a black screen.

But, I'm puzzled, because I was able to use Karmic Koala RC on my Asus P5QL Pro and GeForce 9500 GT. No X crash. 


I was just wondering if the problem could be the optical drive, some just randomly stop when in middle of a reading until warmed up. (One of my Lite On CD drives hate it when I keep my PC case real cool!)

---

### Post by lyeberry on 2009-10-31
I get the same problem on 2.6.31 kernel. After AppArmor, karmic will freeze and jus spit out a soft lockup bug.

---

### Post by datacrusher on 2009-11-11
same problem here. Tryed:
- boot on rescue mode
- boot on rescue mode, adding init=/bin/bash, no go.

---

### Post by gomerclaus on 2009-11-12
I just started getting the same problem.

I had installed Karmic last week, and everything was going fine. Then I did something n00b stupid earlier today... During boot, a routine partition check detected some problems, so I ran fsck. Except that the partition I was checking was currently mounted. As it turns-out, this was a bad move. I proceeded to completely hose my installation. Meh. Stuff happens. I'm over it... Or else I would be if the installer would move past this cursed alien dotted-circle Ubuntu logo.

I'm going to try the alternative installer right now, but if the previous posts are any indicator, I won't be having much luck.

/sigh

---

### Post by gomerclaus on 2009-11-12
Yep. Didn't work.

Bump.

---

