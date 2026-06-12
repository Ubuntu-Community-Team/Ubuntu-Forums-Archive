---
title: "ATI 9800 performance drop in karmic"
date: 2010-01-09
forum: Hardware
---

### Post by DRF on 2010-01-09
I've got an ATI 9800 and recently I've replaced the hard drive in my computer and done a fresh install of ubuntu hardy (LTS), Debian Stable and ubuntu karmic.

But I've noticed a huge regression in the open source radeon/ati drivers performance in karmic which surprised me and I wondered if there was some change to the default xorg config that caused this sudden regression.

Comparing ubuntu 8.04 to 9.10:
8.04 compiz worked, 9.10 compiz fails.
8.04 extreme tux racer worked reasonably, 9.10 extreme tux racer worked but at a frame rate that made it unplayable.

Both installs had the xorg ati and radeon packages installed. I compared the results of glxgears and got:
18926 frames in 5.0 seconds = 3785.130 FPS with ubuntu 8.04
1013 frames in 5.0 seconds with ubuntu 9.10

Both versions of ubuntu start their glxinfo data with:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

The xorg.0.log files show some differences worth mentioning:
8.04 has the line: "RADEON(0): Using XAA acceleration architecture"
9.10 has the line: "RADEON(0): Using EXA acceleration architecture"
8.04 has the line: "RADEON(0): Using AGP 8x"
9.10 has the lines: 
"RADEON(0): [agp] AGP not available"
"RADEON(0): [agp] AGP failed to initialize. Disabling the DRI."
"RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module."
(lsmod shows agpgart loaded and used by ttm,drm,amd64_agp)
"RADEON(0): Direct rendering disabled"
"RADEON(0): Render acceleration enabled for R300/R400/R500 type cards."
"AIGLX: Screen 0 is not DRI2 capable"
"AIGLX: Screen 0 is not DRI capable"

I was surprised to see this regression in karmic and if anyone has any suggestions on how to fix this or knows of some common config change that is needed that I'm unaware of I would appreciate any help.

Daniel

PS. If any further logs or information helps feel free to ask, depending on what replys I get I might well file this as a bug also.

---

### Post by DRF on 2010-01-09
Just an update to say that on a hunch after posting this I enabled the ctrl+alt+bksp key combination and restarted X in case the issue I've been having is simply to do with modules loading out of order or too soon after each other and this does seem to be the case as after doing so glxgears is now showing: "18257 frames in 5.0 seconds" which is a huge difference to what I was getting previously. So if anyone else is also seeing poor performance I would suggest trying this to see if it fixes it for you.

Hope there is a way to change/fix the module loading issue to remove the need to restart X.

Daniel

---

### Post by derekmbarnes on 2010-01-09
You want to tell the rest of us how to do everything you just did? I've been lagging just trying to run Tetris. (And there are other issues that may or may not be related.)

---

### Post by DRF on 2010-01-09
When I went to file a bug I discovered a bug report that I had overlooked previously so it has been reported already and is bug #468413 on launchpad if anyone wants to mark themselves as being affected and read the comments on the bug report which include some suggestions on ways to work around the bug.

The steps to test if this is indeed the bug your experiencing is to check your 3D performance using something like 'glxgears'. (Applications -> Accessories -> Terminal Type in glxgears and make a note of the number of frames in 5 seconds which it will display in the terminal window)

Go to System -> Preference -> Keyboard choose the Layouts tab and click on the Layout Options button. From the Options window that appears maximise and put a tick in the option 'Key sequence to kill the X server'.

Now pressing 'Ctrl + Alt + Backspace' will restart the X server (make sure to save anything your working on as it will take you back to the ubuntu login screen).

Try running glxgears or other similar program your using to test your performance and if you see a noticeable improvement your probably experiencing the same issue. (reading xorg.0.log from System -> Administration-> Log File Viewer will confirm it if it contains similar warnings about AGP not available)

Hope this helps you to diagnose your lagging issues.

---

### Post by DRF on 2010-01-16
Just an additional note to say if the previous didn't work a more certain method is to open a terminal and type:

sudo modprobe -r radeon
sudo modprobe radeon
sudo restart gdm

This is more likely to work than the previous post. Same warning applies that anything you had open and wasn't saved will close when the X server restarts.

Daniel

---

