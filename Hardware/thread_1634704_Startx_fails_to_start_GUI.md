---
title: "Startx fails to start GUI"
date: 2010-11-30
forum: Hardware
---

### Post by Jason Spaceman on 2010-11-30
I upgraded to Ubuntu 10.10, but the GUI interface fails to start when the computer boots.  Instead I get a command line prompt, when I log in and type 'startx' I get the following (copied from the Xorg log):

> [   269.667] (WW) Falling back to old probe method for v4l
[   269.667] (--) NV: Found NVIDIA GeForce Go 7900 GTX at 01@00:00:0
[   269.668] (EE) NV: Kernel modesetting driver in use, refusing to load
[   269.668] (EE) No devices detected.
[   269.668] 
Fatal server error:
[   269.668] no screens found
[   269.668] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   269.668] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   269.668]

Is there a way to fix this?

---

