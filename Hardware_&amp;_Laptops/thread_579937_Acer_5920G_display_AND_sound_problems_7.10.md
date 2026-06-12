---
title: "Acer 5920G display AND sound problems 7.10"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by thegr8brian on 2007-10-18
Hello everyone, I am very new to Linux but am a long time windows user having built and overclocked computers and so forth...but my Linux knowledge thus far is not the greatest, however I am a first year computer engineering student and I feel that it is time to switch or at least get acquainted with Linux.  So I am currently making this post while running 64bit Gutsy Gibbon on a live CD...The first problem I ran into was when asked to choose what mode to start in at the CD boot, I chose the top one but after taking a while it said my display settings could not be configured and I was forced to run in low graphics mode...so I rebooted successfully with safe VGA mode...would this be a problem specific to running from a live CD or would it be resolved upon installation(See Specs below).  Also I noticed something strange regarding sound, I can for some reason hear sound only through the headphone jack, not through my laptops built in speakers.  In the volume controls there was a tab that had a check box with the word headphone next to it, both ticked and unticked sound would only come through the headphone jack...Is this a live specific problem or could it be resolved upon installation?...I just want to know these things will work before I go off and install the operating system...everything else seems to be fine though...Nice release!
 
Acer 5920G
Intel Core 2 Duo T5250 1.5ghz
4gb DDR2 ram @667mhz
Nvidia 8600m GT 256mb
15.4in Widescreen LCD Display 1280x800 native
160gig 5400rpm HDD
Realtek HD Audio

---

### Post by thegr8brian on 2007-10-18
I also just noticed that my volume control on the laptop is controlling the line-in volume rather than the "front" volume...what could be the cause of this?

---

### Post by thegr8brian on 2007-10-18
:confused:

---

### Post by JimmyK377 on 2007-10-20
I have exactly the same issue as the one at the top there, my system is the same except for the T7300 2ghz CPU.

---

### Post by JimmyK377 on 2007-10-20
and amusingly enough, I'm also a first year student, of computer science (slightly different) making the switch after many years of windows, but anyway, does anyone have any idea as to the problem, I note even it just stops doing anything after the battery and boot files check, shortly after having been unable to detect the video hardware

---

### Post by JimmyK377 on 2007-10-20
As I've yet to see this issue with the 32-bit ubuntu installation I'm thinking maybe it's just an issue with the 64-bit one.

...

Anyone?

---

### Post by JimmyK377 on 2007-10-21
The 32 bit version doesn't have the display issues. Just using that instead seems to solve it.

---

### Post by DrunkDelirium on 2007-11-05
I had the same problems with the sound but got it working after some messing around (pure linux newbie here) in Ubuntu 7.10 on an Acer 5920g. My solution:

Open volume control (double click on the speaker icon in the upper right corner of the screen)
In volume control make sure that in File -> Change device the "HDA Intel (alsa mixer)" is selected.
Go to Edit -> Preferences and select all tracks in the list.
Unmute and increase volume on "PCM", "Surround", "Center", "Side" and "LFE". Sound should work nicely now. Optionally mute the micophone sliders.

---

### Post by Bou on 2008-03-16
My girlfriend just bought a 5920g and thanks to you she can use Ubuntu so thanks a lot mate, I owe you! :)

---

