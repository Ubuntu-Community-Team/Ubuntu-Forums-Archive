---
title: "Booting without primary monitor hangs system"
date: 2009-08-24
forum: Hardware
---

### Post by fuzzyllama on 2009-08-24
I have been using Ubuntu for about 3 years as a headless server.  Recently, my wife's laptop broke and I had the idea to plug the server into the family bigscreen in the living room to give her the net access she needs, and to keep her from hoggin' my box!

I had the 8.04 release up and running in GUI mode in a few minutes.  By editing the x.conf file I was able to get login screen to show on the LCD TV no problem.  There was a weird sound issue where my SB card would not get detected coming back from hibernate, and several other sound-related problems.

I decided to upgrade to 9.04 to fix the sound issue.  Install went perfectly, sound works, even Flash works without having to run Firefox in Wine.  Unfortunetly, if I do not have a monitor plugged into the primacy output of the Video Card, the boot hangs and will NEVER bring up the login on the TV.  To make matters worse, I can't even ssh into the box when it is hung.  If I simply plug a monitor into primary [VGA], the initial boot menu shows up on monitor 1, then the splash shows on monitor 1, then monitor 1 loses the signal, and monitor 2 [DVI] pops into life. 

I'm frustrated, and with Wolfenstein coming out Thursday, I need to get this fixed ASAP so I can get some serious time in without having to take "breaks" - so she can check her e-mail or facebook...HELP!

---

### Post by fuzzyllama on 2009-08-25
I spent several more hours yesterday, and I think I've narrowed it down even more... 

This was working 100% again last night.  Then when I tried to log in today..nothing...just a blank, black screen.  It turns out that my wife had put it into power save (screen saver on for more than 40 minutes/idle).  I tried it several more times, and it always fails when coming back from power-save mode, but works otherwise.  Not sure what has broken, but this worked A-OK in Hardy.

---

