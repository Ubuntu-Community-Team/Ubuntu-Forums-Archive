---
title: "Toshiba Tecra S1 - Edgy, Beryl and so on."
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by TmP on 2006-11-26
Hi!

This is to all owners of Toshiba Tecra S1 ( and I know there are still a few of us left). 

If your considering Linux but are in doubt if it works on your laptop, than no worries. I've been using the 3 past releases of Ubuntu and found it mostly satisfying to run on Tecra S1.

Ive been running Ubuntu as a dual boot, along the WinXP. It fits the 40Gb  provided disk (10GB for windows, 10GB for Ubuntu's main partition "/" , 500mb swap, 5Gb for home and ~15GB for files and stuff that windows sees as a second disk and Ubuntu as just another partition that happens to be a FAT32).

The reason why I recommend leaving WinXP and using dual boot is the lack of support for "power themes" i linux. Because of that, in windows you can work longer on batteries by switching your machine to lowest performance. 

The common issue with laptops under Linux is that you cannot change the brightness of the screen straight from the box. This applies to Tecra S1 as well. There seems to be a solution for this, but involves messing with the  Linux kernel and I haven't the time. If any of You Tecra owners figgured out how to solve this, pleas post it here. 

When it comes to accelerated graphics, the route is a bit thorny. Mobility Radeon 9000 is not that well supported out of the box. And let's be frank - it is not a very fast... 

Lately I have managed to get Beryl running - through this great guide:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It is not only a showy desktop - it is actually useful - for instance you get a wonderful application switcher that scales all your open windows on a screen and lets you choose one. You can't forget about it's jaw-dropping-screw-Vista-tell-me-how-to-install-Ubuntu factor (Literally: I am using Aero theme that's worth 200$ and shouldn't be possible to run on Tecra S1 according to Microsoft) . Still it is full of bugs, and collides with other GL applications, so better not put it on start up but run it from console instead. Just type "beryl-manager" and you can close the console). 

For Tecra it is easyest to run Beryl on AIGLX. The overall performance is rather poor, but when you turn off the gizmo's like the rain (which does not work on 9000), blur and some annoying animations, Tecra manages to stay above 30 fps. It is likely that Beryl would run faster on FGLRX but be advised that there is some kind of a bug that prevents the "direct rendering". There are many how-to's around, that will break your X windows. If you find one that works, please point me to it. 

Hope this helps. I wasted a lot of time looking for my specific machine on the forums. Hope you won't have to.

---

