---
title: "Touch screen calibration lock ups and software on small resolution issues"
date: 2009-09-28
forum: Hardware
---

### Post by Truenash on 2009-09-28
Hey, both of these problems are on an Asus T91, using Ubuntu Netbook Remix 9.04. I have posted both of these issues in the Asus T91 installation thread, but haven't had much success, so I thought I'd open it up to a bigger audience.

With the T91, when starting the calibration software for the touch screen, the instructions come up, then black screen, then a calibration finished message. If you know of any alternative method of calibration or can help with this, that'd be great.
The terminal reads:

```
/usr/bin/ev_calibrate 
evalibrate located at /usr/bin/ev_calibrate 
xinit located at /usr/bin/xinit 
xserver located at /usr/bin/X 
Creating FIFO... 
Starting calibration program... 


X: warning; process set to priority -1 instead of requested priority 0 

X.Org X Server 1.6.0 
Release Date: 2009-2-25 
X Protocol Version 11, Revision 0 
Build Operating System: Linux 2.6.24-23-xen i686 Ubuntu 
Current Operating System: Linux nash-eeet91unr 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 
Build Date: 13 May 2009  03:38:35AM 
xorg-server 2:1.6.0-0ubuntu15~904um1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org 
	to make sure that you have the latest version. 
Markers: (--) probed, (**) from config file, (==) default setting, 
	(++) from command line, (!!) notice, (II) informational, 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) Log file: "/var/log/Xorg.1.0.log", Time: Mon Sep 28 16:27:07 2009 
(==) Using config file: "/etc/X11/xorg.conf" 
(EE) PSB(0): the stolenBase is:0x7f800000 
(EE) PSB(0): screnIndex is:0;fbPhys is:0x7f800000; fbsize is:0x007bf000 
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!! 
(EE) [drm] Could not set DRM device bus ID. 
(EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI. 
(EE) [drm] Could not uninstall irq handler. 
(EE) PSB(0): This driver currently needs DRM to operate. 

Fatal server error: 
AddScreen/ScreenInit failed for driver 0 


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org 
 for help. 
Please also check the log file at "/var/log/Xorg.1.0.log" for additional information. 

 ddxSigGiveUp: Closing log 
giving up. 
/usr/bin/xinit:  No such file or directory (errno 2):  unable to connect to X server 
/usr/bin/xinit:  No such process (errno 3):  Server error. 

```


This issue also happens as the system is shutting down. I followed the guidance of a bug report for a similar issue, uninstalling and reinstalling the psb driver, but this didn't help.

The other issue is that Inkscape, Xara and a few other programs do not maximise properly on the 1024 x 728 resolution of the netbook. I had heard this issue was fixed, but apparently not.

Any help on either issues would be greatly appreciated.
Thanks in advance!

---

### Post by Truenash on 2009-09-29
Shameless bump

---

### Post by DLotus on 2009-10-03
Hi Truenash, I got one the other day. Installed 9.04 (not the remix, sorry didn't try that) I went to synaptic and search touchscreen. I then installed everything listed with libts (description should be touchscreen library), xserver-xorg-input-evtouch and xserver-xorg-input-tslib. 

After that I went to Preferences, Calibration tool and it brought up a grey screen with crosshairs in each corner, tap those, Works great since then. Good Luck :)

---

### Post by Darthkatzs on 2009-10-08
Were you able to fix this? Cause I'm having the same problem.

---

### Post by cantormath on 2009-10-29
Any words on how the t91 performs using ubuntu?  Does it seem faster then the preinstalled windows, the same.....etc?  Any apps poor performance?

> **DLotus said:**
> Hi Truenash, I got one the other day. Installed 9.04 (not the remix, sorry didn't try that) I went to synaptic and search touchscreen. I then installed everything listed with libts (description should be touchscreen library), xserver-xorg-input-evtouch and xserver-xorg-input-tslib. 

After that I went to Preferences, Calibration tool and it brought up a grey screen with crosshairs in each corner, tap those, Works great since then. Good Luck :)

---

### Post by LukeKendall on 2009-12-15
> **Darthkatzs said:**
> Were you able to fix this? Cause I'm having the same problem.

I started posting this, because I was having the same problem, but I've found how to workaround the problem pretty easily.

I'm running Ubuntu netbook remix 9.10, with the GMA500 graphics driver installed (poulsbo).  I got the touch screen working basically by installingxserver-xorg-input-evtouch via synaptic, but the calibration fails almost exactly as you describe (I have a different hex address for the "stolenbase".

Then I also tried Dlotus's advice:

> I then installed everything listed with libts (description should be touchscreen library), xserver-xorg-input-evtouch and xserver-xorg-input-tslib.

(except I didn't install the libts stuff related to debug and developers)
But the calibration tool won't run.  If I run it via gksu /usr/bin/calibrate_touchscreen from Terminal then I see all the errors.

So, no luck there either.

Someone mentioned that the DRM error meant the driver couldn't run with a server already running.  I tried to see if I could start it on a new screen by temporarily modifying that script to change MYDPY manually to ":2.0", but that made no difference.

So I rebooted in safe mode to get a terminal window without X running, and **was** able to run the calibrate_touchscreen from there.  After 5 mins of trying to make that work, I found a place on the web that had the text of the instructions of what to do, here:
[https://wiki.ubuntu.com/JauntyTouchscreenHandling](https://wiki.ubuntu.com/JauntyTouchscreenHandling)
and from there I could complete the steps required by the calibration program.

(Short summary: trace all around the touchscreen. Then hit Enter to signify you've finished that 1st step.  You may need to hit Enter again if nothing happens.  Then the top left calibration mark turns red, meaning you should press on that.  Ditto for all the others.  When you click on the last one, the calibration finishes and you drop back out of the X calibration.)

But when I finished, it exited and then gave a stack backtrace.
I checked, and the xorg.conf file had not been modified (which is what I expected would happen, but later learned that my idea about that was wrong).

I assumed it hadn't worked, and ran it again to capture all the output, which included a bunch of dx and dy values, prepared to follow the advice here:
[http://ubuntuforums.org/showthread.php?t=419235](http://ubuntuforums.org/showthread.php?t=419235)
and try to use that info (I think, now, that would have been a mistake), but when I rebooted, the touch screen was perfectly calibrated.  A find on /etc showed that the file /etc/evtouch/config had been created, and all is now good.

luke

---

