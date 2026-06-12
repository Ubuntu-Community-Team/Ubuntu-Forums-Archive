---
title: "Dell E6410, i915 very unstable"
date: 2011-01-21
forum: Hardware
---

### Post by mbeierl on 2011-01-21
I cannot keep the OS running for more than one day without some form of X hang.  From frozen at a black screen to getting GPU hang reports in the Xorg log.  The latest one is this:

```
[ 20731.300] (EE) intel(0): failed to set mode: Input/output error
[ 20731.300] 
Fatal server error:
[ 20731.300] AddScreen/ScreenInit failed for driver 0
[ 20731.300] 
[ 20731.300] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[ 20731.300] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[ 20731.300] 
[ 20731.355]  ddxSigGiveUp: Closing log

```

I have been using Ubuntu since 5.04 and have not been this stumped in a long time.  Can anyone help shed some light on what is wrong with my installation, please?

---

### Post by mbeierl on 2011-01-25
I also have the problem of the screens "missing" a section which I can't seem to get back.  There is a section of about 40 pixels which disappears between the two monitors - see screenshot.  

The weird thing is the mouse does not go into the missing section - it immediately moves to the next display.  The right-hand monitor also has the mouse location offset by the 40 pixels as well.  An attempt to explain it: the display of the windows and desktop is offest by 40 pixels, however the actual location is correct according to what the mouse can hit.  In other words, I need to go 40 pixels to the right of any object on the right-hand monitor in order to hit the object.

Anyone?

---

