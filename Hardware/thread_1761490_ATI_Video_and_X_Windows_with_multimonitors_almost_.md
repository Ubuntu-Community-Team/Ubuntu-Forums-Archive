---
title: "ATI Video and X Windows with multimonitors almost unusable"
date: 2011-05-18
forum: Hardware
---

### Post by egandt on 2011-05-18
I have an HP Workstation its a sandybridge system 2600 with 12GB RAM at work.  It consists of 4 PCI-E slots 1 16x and 3 1x slots, now I have 3 monitors as follows:

#1 1920x1080 23"
#2 1920x1080 23"
#3 1600x1200 20"

I hence I need 2 video cards (as non are displayport and all flicker when hooked up to an active display port adapter, thanks for that AMD).  I have tried:

5570x16 and x1300x1: Failed as the x1300 is not recognizedly in X only by the command line utility, which is somewhat understandable given the age of the x1300
5570x16 and 4550x1: Fails, crashes X when you enable a screen on the 4550 in PCI-E 1x slot
5450x16 and 4550x1: Fails, crashes X when you enable a screen on the 4550 in PCI-E 1x slot
4650x16 and 4550x1: Hey this works, which is great, but the monitors connected to a single card but be placed next to each other in order for it to operate correctly, (AKA if 1 and 2 are on the 4650 and 3 is on the 4550 then if I place them 1,2,3 it works, but 1,3,2 will result in monitor 2 not being used.  2,3,1 results in monitor 1 not being used ...).

So now I know that mixing 5 series and 4 series cards does not work with the 11.4 drivers, but using all 4 series cards mostly works.  Yet there is a problem, since this is a workstation class system from HP, you do not have the Power Supply to run any powerful video card, and all the entry level cards have 1 HDMI, 1 DVI and 1 VGA, or else 1 HDMI, 1 DVI, 1 DisplayPort.  Either way that means 1 monitor must be connected to the HDMI port, that is annoying but fine so 1 HDMI to DVI cable later it works.  Well it kind of works, if you do not let the display sleep and screen saver for all monitors is disabled.  Otherwise once the monitor connected to the HDMI port goes to sleep it never wakes up again, and you need to log back in, sometime unplugging and plugging the cable in works (say 50% of the time).


So we have discovered 3 major issues with AMD's 11.4 (and all the way back to 10.9) Linux Drivers:
1. mixing series (such as 4 and 5) does not work
2. mixing an x1300 with any other generation does not work (I can understand this since is it a completely different arch).
3. HDMI connected monitors have issues with losing signal when monitor sleeps.

Now all of these are easy to diagnose and solvable QA, issues that could and should have been fixed, but are not fixed and for the life of me I can locate no way to open support tickets with AMD to request they resolve these stupidly simple issues, that only effect Linux (as any combination above except for the x1300 which I did not try works without issue on Windows XP and 7).  If I had been able to open a case with AMD I would have, but as that is not possible I figured the next best was to post my finding to help anyone else encountering similar issues and maybe some day someone for AMD will review this post and fix an actually bug.

ERIC

---

