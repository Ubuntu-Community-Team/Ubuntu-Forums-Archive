---
title: "Hybrid Graphics: Just want to use the integrated card"
date: 2014-01-15
forum: Hardware
---

### Post by matthiask on 2014-01-15
Hey folks,

I've installed Ubuntu 12.04.3 x64 and been struggling with Hybrid Graphics the last three days. I tried different guides, especially this one [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) but had lots of problems with fglrx e.g. black screen with blinking cursor, low-graphics mode after reboot. Had to reinstall the system after that.
This guide ([http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)) looks slightly different but I didn't try it yet because they are written for higher versions of Ubuntu.
I've read through a lot of those threads (also about switcheroo, radeon, prime) but I don't think that I got it all sorted right. Far too much information out there...

My current problem is that I have a muxless Hybrid Graphics system (Dell Vostro 3550, Intel HD3000 + Radeon HD7650M) and Ubuntu with its standard driver (VESA: Intel Sandybridge Mobile Graphics) doesn't allow me to chose a resolution > 1024x768. What I want to know is whether it is possible to just deactivate the discrete card and only use the integrated Intel HD3000. I don't think that I will need the HD7659M, so before messing around again and throwing away 20 more hours I'd hope to get some useful information from you guys! 


Thanks in advance!

---

### Post by matthiask on 2014-01-16
Update:

I found out that it is possible to deactivate the discrete card via vgaswitcheroo. There are several how-tos on the web and as many people writing that it's not working for them because it says "*No such file or directory"*. Same applies to me when I do [COLOR=#993366]*# cat /sys/kernel/debug/vgaswitcheroo/switch*[/COLOR]
Even tried *[COLOR=#993366]# sudo mount debugfs none /sys/kernel/debug[/COLOR]* like it's suggested here [http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/](http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/)

How is it possible that there is no switcheroo in the kernel? It's a fresh install didn't mess with any fglrx or other things. The open source driver radeon seems to be active though I can't change screen resolution as described above.

Anyone able to help me please?:(

---

