---
title: "DVI signal is lost after inactivity and does not recover"
date: 2008-06-18
forum: Hardware
---

### Post by hagak on 2008-06-18
So I have been working on getting this new motherboard working and have tried many things to fix this odd issue with the DVI signal stopping after some period of time.  Note the VGA signal has yet to experience any issue.

The hardware:
Gigabyte ga-ma78gm-s2h 780G (using the IGP for video)
2GB RAM
Athlon X2 4600+
Monitor Viewsonic VP171b LCD (has both DVI and VGA inputs)

Running from the LiveCD this problem does not exist so I suspect the problem is related to the ATI drivers since those are not loaded on the LiveCD.

I installed ATI 8.5 drivers from ATI.  I have tried both Clone display and Single desktop display.  I have disabled the screensaver.  I have forced the vrefresh to 60hz mainly because without doing this it kept setting the refresh on the DVI to 75hz and this seemed to cause corruption in the video.  I also made sure to set the only mode option in xorg to just the native res of 128x1024.

At first I thought the issue was related to DPMS so I tried to force the problem by using xset to force the monitor into off state, also forced it to both standby and suspend to see if any of these caused the issue.  They all worked fine and the display woke back up as it should.  The issue only seems to happen when I leave the machine for an hour or more. (powersave is set to 20 minutes for sleeping the monitor, I do not suspend the machine).

So what happens is the DVI output seems to just stop functioning after inactivity and will not come back until AFTER I power down the machine and power it back up, rebooting does not fix it.  VGA has no issues and when the display is non-responsive I can switch to VGA input(if it is in clone or mirror mode). I also can ssh into the machine fine.  I have not seen anything in the xorg logs detailing this DVI shutdown.  Again if I use the livecd I have not had this happen even after 8 hours of inactivity.

So my question is could this issue be a hardware problem?  If so I have no issues returning it, I bought it from Microcenter who are great with returns.  Heck as I write this I think I may just do that anyhow, spent a week so far messing with this.

So anyone seen anything like this?

Edit: Forgot to mention using ubuntu 8.04 AMD64 version.

---

### Post by hagak on 2008-06-18
Well after looking around at what motherboards are available that have IGP (this is to be an inexpensive setup and not used for heavy 3d) not sure what I would exchange the board for?  Should I just see if it is a hardware defect and get the same board replaced?  Or try a board based on the nvidia 8200, however after seaching here a bit the 8200 does not seem to be supportted by linux too well.

Note I have this same board working very well as a HTPC, however that is running XP.

---

### Post by hagak on 2008-06-18
Update on the problems.

I can reproduce the problem.  It seems to be tied to the screensaver and sleep.  If I just sleep the monitor it seems to be fine and come back fine.  However if I have a screensaver set currently uses "Blank" at 10 minutes, and then the display set to sleep at 20 min.  When the display goes to sleep it will not wake up again.

I am ok not having a screensaver, normally do not use them anyhow just use monitor power saver.  However I then tried another test, I turned off the screensaver but decided to run the preview of the screensaver (this time glmatrix) and let the display sleep.  When the time was up for the display to sleep it did NOT sleep instead the screensaver seemed to lock and the machine seemed to be unresponsive.  However I could still ssh remotely into the machine.

Does anyone think this could be a hardware issue?  If so I will swap out the board, however that is a decent bit of work and a 40 minute drive.

Any input welcome.

---

