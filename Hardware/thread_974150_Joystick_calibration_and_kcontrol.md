---
title: "Joystick calibration and kcontrol"
date: 2008-11-07
forum: Hardware
---

### Post by FokkerCharlie on 2008-11-07
Hi All

I have been using an ageing (but actually quite good) Logitech Wingman Extreme 3D for some time, mostly for playing FlightGear.  The only way that I have been able to correctly calibrate the device has been by using kcontrol.  jscalibrator appeared to calibrate the joystick OK, and showed all the right outputs while the program was running, but after starting FG, the joystick did not respond at all.

Unfortunately, since upgrading to Intrepid, kcm_joystick has not worked.  I get this error on running:

> The Specified library joystick could not be found.
The diagnostics is:
Library files for "kcm_joystick.la" not found in paths.
Possible reasons:
- An error occurred during your last KDE upgrade leaving an orphaned control module.
- You have old third party module lying around. 

Check these points carefully and try to remove the module mentioned in the error message.  If this fails, consider contacting your distributor or packager.

It looks like kcm_joystick was removed during the upgrade to me.  It isn't installable any more from the repos.  Has it been replaced with something else I can use, apart from the command-line util?

Cheers
Charlie

---

