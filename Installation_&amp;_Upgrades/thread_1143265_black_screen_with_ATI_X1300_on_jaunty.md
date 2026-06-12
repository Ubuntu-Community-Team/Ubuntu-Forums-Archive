---
title: "black screen with ATI X1300 on jaunty"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by flamarro on 2009-04-29
Hi guys,
After all the readings i have done about ATI, i don't know, again what else can i do...
Jaunty, clean install, managed to install it with the VGA option, restarted, at the end... black screen...
Had to started in safe mode changing the driver to vesa.
Done all that of removing all fglrx stuff from the system, couse my x1300 doesn't have a proprietary driver now, have erased /etc/ati directory, done the command “sudo apt-get remove –purge fglrx*”' and changed the driver to ATI in xorg.conf, like it was said [[COLOR="DarkOrange"]here[/COLOR]]("https://wiki.ubuntu.com/Bugs/AtiDriver") and [[COLOR="DarkOrange"]here[/COLOR]]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver"). Pressed ALTgr+printscreen+K and beautiful, even compiz works, but as soon i reboot, without changing anything, at the end blackscreen again.... I repeat  all this procedure again, sometimes works, others don't, but as soon I reboot, black screen again. One way it always works is with driver vesa, no problem here..... no compiz or some hardware acceleration, but works...
I am really desapointed with this ATI issue... As i always remember, every 6 months I have this problem, have to understand what i can do with a new version of ubuntu so that my damn ATI works... 
I have read lot of stuff on this, tried so many things, change a lot in xorg.conf, but no success, at the end a black screen, sometimes I know the computer is working, because I can do ctrl+f1 and change xorg, sometimes I get a black screen with some blinking pixels and have to turn it off, because it has crashed.
I dont mind if I have to work with open drivers or closed ones, as far has they work, it's enough for me.

---

### Post by flamarro on 2009-05-06
ok,
i was about to give up, i was so mad with Ubuntu that i was using much more the other OS, only coming to ubuntu to try something else after reading more of the forum.
Watching line by line on xorg.log.0 i saw something about display 0 and display 1, suddenly i remember that i have a monitor connected at VGA output and a tv connected at SVideo output. Disconnected the tv cable and restarted and \\:D/ .
I am now with a clean install working pretty good indeed even with compiz working with no need of tweaking something. The driver that i am using is ATI. No blinking and i can use mplayer without the need of turning off compiz. amazing. Now, i can upgrade my other partition with 8.10
Now, to the other battle, use ATI driver with tv out. As i have read, i think that a no work yet, is this true?

---

