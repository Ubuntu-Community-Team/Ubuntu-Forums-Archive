---
title: "lubuntu(15.x.x) suspends randomly!!!!"
date: 2015-09-09
forum: Hardware
---

### Post by irongolem0982 on 2015-09-09
sorry if this is in the wrong section. its a little bizarre at this point....

so i installed Lubuntu 15(something) on a dell inspiron 700m old laptop. it actually had the same version(of lubuntu) installed about a week ago and i had to wipe the whole thing cause of a windows error. it ALSO had this same symptoms and error before but i don't remember how i solved it!!! bottom line, heres what happened

this morning i stuck lubuntu on a flashdrive and attempted to boot on the desired computer. wouldnt work!! it kept suspending every few seconds during the boot process. (i used unetbootin, and selected the "install lubuntu" option) so i plugged it into my other computer that im using right now and booted on it. it worked just fine! and i ran "sudo apt-get update" followed by "sudo apt-get upgrade" just so my flashdrive was 100% up to date. then i plugged it back into the other pc and attempted to boot using the same option("install lubuntu") it still kept suspending every few seconds and i kept turning it on every time for about 10 minutes. so i tried the "try lubuntu without installing" option and this time it only suspended 5 or 6 times before it got to the home screen where it stopped the suspending loop and just sat there. so i proceeded to install lubuntu and all went well (i did run into some snags but not related). on reboot it still suspended every few seconds until it was fully booted then it would stop and i could continue my work without the interruption. until later today while i was using the computer to cue music for a play (right in the middle of a song.....) and i accidentally opened "light locker" instantly after clicking on it the computer suspended. i turned it back on and about 30 seconds later it suspended again. it now does this constantly. every 30 seconds it suspends. its really annoying! 

the intervals are at exactly 30 seconds(stopwatched and all)

so far ive tried:
 disabling light locker
uninstalling light locker
multiple reboots
reinstalling xfce4 power manager (which i had used just fine before everything else)
running a few commands from other fourm posts. none work.
i attempted to use ctrl+alt+f1 and get a video of what the kernel was saying but my camera didnt work. it kept suspending even in ctrl+alt+f1. 
inside ctrl+alt+f1 it spams every 3 seconds: [B][time] [drm:intel_cpu_fifo_underrun_irq_handler [i915] *ERROR* CPU pipe A FIFO underrun]
[/B]i googled that and found that it is a video card error and that i needed a different driver. but the download is broken (at least the one i found).
i dont even know if the above error is related. and i cant really see what is causing it to suspend cause it goes so fast.

right now i type about 106 wpm so i can type a few commands before it suspends, any effort helps!!!!

---

### Post by irongolem0982 on 2015-09-09
GOSH!!! NVM..... i fixed it... apparently xfce4-power-manager dosent take over after light locker is uninstalled. i went to the security page in xfce4 and turned everything off there. then turned everything back on a minute later and boom! stopped suspending. im posting from the affected computer now. my question now is. one of the things i tried was going to /etc/xdg/autostart and deleting power manager. how do i get it back? and since light locker is uninstalled should i delete screenlocker.desktop???

---

### Post by Jacob_Zhang on 2015-12-26
idk how to get it back, but holy **** I had the exact same problem. I too installed Lubuntu on a Inspiron 700m and one day it started to randomly suspend. The problem was that it was rather difficult to diagnose the problem when every few seconds your computer would suspend. Thanks for the fix.

---

### Post by yoshii on 2015-12-26
I think you have to download power manager from a terminal or from Lubuntu's download manager, whatever that is.  Typically, just deleting stuff causes instability.  It's safer to use "sudo apt-get remove" or "sudo apt-get purge" to delete system components and their dependencies and update the indexes.  When you just randomly delete stuff, the system thinks stuff is still there, tries to find it, has an error, and something fails.  The purge command removes the preferences along with the rest of the stuff.

---

### Post by Jacob_Zhang on 2015-12-27
A quick solution for anyone who has this problem: 
There's a small button on the top right hand corner of the Inspiron 700m to tell if the screen lid is closed. Once you boot up the computer, including from suspend mode, hit it a couple times. The screen will flicker once or twice (as if you closed your lid) and just like magic no more suspending will happen. Not sure of the workings behind this.

---

