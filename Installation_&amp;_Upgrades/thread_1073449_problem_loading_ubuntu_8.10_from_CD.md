---
title: "problem loading ubuntu 8.10 from CD"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by axel_2078 on 2009-02-18
I've noticed that many people, including myself, have had problems installing Ubuntu 8.10 from CD due to freezing during the load phase, usually caused by "buffer I/O Errors on Device sr0". Why is this? I know the image (.iso) itself is good because I've installed Ubuntu 8.10 successfully into a virtual machine on Windows and on a Mac using that same image without a problem. I've since burned that image to CD three times now and keep having the same "buffer I/O errors on device sr0" that keeps the CD from booting successfully on my laptop. I get this same error message no matter which option I choose (test disk for errors, try out before installing, install, etc). I normally hit F6 and take the quiet splash off the boot line so I can see what's going on during the load and it seems to stop because of the sr0 errors. It eventually just reaches a point where it stops trying to load anymore and just hangs. Now, If I try to load it up using the F6 option and add "noacpi" to the boot line paramaters, I still get tons of sr0 errors, but it will keep rolling through until it boots to the desktop.

Here's what I noticed while troubleshooting/researching: Many other people that encountered this same problem say they solved the problem by doing one of two things; burning the image at a slower speed, or replacing their optical drive with a different one (it seems that some optical drives can't buffer fast enough?). My optical drive works fine under Windows XP and I've managed to load various other Linux distros onto it, including an earlier version of Kubuntu (Gutsy). This is the first time I've ever had a problem getting a Linux disk to boot successfully. What gives? Why are so many people having this same problem?

I tried another disk burned at 2X on my work laptop to see what would happen. I selected the try before install option and used F6 and removed the quiet splash option so I could see what was going on. I still got lots of sr0 buffer errors, but it kept rolling through until the desktop loaded. From what I've researched so far, Ubuntu 8.10 will simply not load on some systems via CD. Why is this? I've certainly never had this much trouble before.

---

