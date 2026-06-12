---
title: "Desktop Screen Trouble"
date: 2014-03-28
forum: Hardware
---

### Post by MikRose on 2014-03-28
I had trouble with my Desktop screen the past few days.  When I start the system, a default Ubuntu Desktop I use appears and the unity icons show on the right side.  But the icons I have added on my Desktop do not show on the screen to the right.  If I go to Firefox for instance, I have no problems viewing websites, emails, etc.  However, if I return to the Desktop, the whole screen now has a black background.  The Unity icons are there, and now my other icons are on the screen to the right.  Yet, all of the icons look as if they have a duplicate image or two superimposed on top of the bottom one....so they are all blurred.  If I have two websites open, and toggle between them, the two screen images quiver until I choose one of them, then the screen is normal.

Here is my graphic driver info:

mik@mik-desktop:~$ lspci -knn | grep -A2 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G965 Integrated Graphics Controller [8086:29a2] (rev 02)
	Subsystem: Intel Corporation Device [8086:514d]
	Kernel driver in use: i915

My monitor is a Samsung SyncMaster S24B30BL
If all screens were garbled I would suspect the monitor, but it works on another system just fine.

Update:  I have done nothing to the system, now it is working as normal....update to follow!

---

