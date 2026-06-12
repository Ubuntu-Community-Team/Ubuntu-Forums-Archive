---
title: "finishes loading then screen goes blank!"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by MasterFateh on 2007-12-20
so i was trying to install ubuntu on my compaq presario f572us and tried with both the x86 and the 64 bit version of 7.10 desktop version but both would randomly stop in the middle of booting from the cd and the cd would completely stop spinning. so i tried the 6.06 LTS ad got the x86 version to load and finally install i partitioned a 10 GB portion of my hard drive for it but after it installed i tried to load it and after loading there was a cursor in the top left corner that blinked once then went to a blank screen. i gave up for awhile and tried it again another time and it worked. but i haven't gotten it to work since then. i don't really know anything about linux so is there a way to boot in recovery mode and put commands in to install new graphics drivers? i can access the partition from my windows xp partition( the rest of the hard drive) the rest of the specs are stock except for 2 GB of ram instead of 1. the specs can be found here: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&cc=us&lc=en&dlc=en&product=3441671&dlc=en&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&cc=us&lc=en&dlc=en&product=3441671&dlc=en&lang=en)

please help

---

### Post by perixx on 2007-12-20
Perhaps you were fooled by Ubuntu, routing the video signal to the _analogue_ out connector, instead of to the digital out/TFT; you can try connecting an analog-based TFT/CRT to your laptop's VGA-connector and triggering the Hotkey for that connector. I had a similar problem with the live-CD and my TFT:
[http://ubuntuforums.org/showthread.php?t=633073]("http://ubuntuforums.org/showthread.php?t=633073")

When being 'stuck', try to press CTRL+ALT+F7 (graphical X-server terminal) or switch to a virtual terminal with CTRL+ALT+F1 (to F4); if you can access it, try either
> sudo startx or
> sudo /etc/init.d/gdm restart
if it works, it will bring up the graphical gdm-login screen.

Perhaps it is also a problem related to this issue:
[http://ubuntuforums.org/showthread.php?t=581075&highlight=long+booting+time]("http://ubuntuforums.org/showthread.php?t=581075&highlight=long+booting+time")

If you can proceed, but have trouble with Grub during your installation, look under this links: 
[http://ubuntuforums.org/showthread.php?t=630714]("http://ubuntuforums.org/showthread.php?t=630714")
[http://ubuntuforums.org/showthread.php?t=621827]("http://ubuntuforums.org/showthread.php?t=621827")
in the post 'Allright, this is where I have it messed up finally... ' and below.

perixx

---

