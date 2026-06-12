---
title: "What is Xorg.0.log telling me in this entry....?"
date: 2011-05-30
forum: Hardware
---

### Post by lumix on 2011-05-30
> 
15.450] (II) LoadModule: "egalax"
39782:[    15.452] (II) Loading /usr/lib/xorg/modules/input/egalax_drv.so
39850:[    15.452] (EE) Failed to load /usr/lib/xorg/modules/input/egalax_drv.so: /usr/lib/xorg/modules/input/egalax_drv.so: undefined symbol: xf86GetMotionEvents
40007:[    15.452] (EE) LoadModule: Module egalax does not have a egalaxModuleData data object.
40097:[    15.452] (II) UnloadModule: "egalax"
40138:[    15.452] (II) Unloading egalax
40173:[    15.452] (EE) Failed to load module "egalax" (invalid module, 0)
40242:[    15.452] (EE) No input driver matching `egalax'


But there obviously *is* a driver matching "egalax".  So what gives?

---

### Post by kacperpl1 on 2011-05-30
> **lumix said:**
> But there obviously *is* a driver matching "egalax".  So what gives?
I think this thread can help You - symptoms are matching yours
[http://ubuntuforums.org/showthread.php?t=1506239](http://ubuntuforums.org/showthread.php?t=1506239)

---

### Post by lumix on 2011-05-30
C'mon...if it was that easy I wouldn't have bothered anyone.  Yes, I did follow that.  It doesn't actually make sense, however, because the person talks about "fresh" installs, but then never adds any new configuration (i.e. to solve the error message problems) except to correct the blacklist entry.  Which I did.

FWIW, I'm not even showing the egalax device in xinput -list, though all other conventional methods of identifying such hardware show the device just fine...usually as connected to event 7.

So what output can I post to provide more useful info?

But thanks for hitting the "reply" button: that alone puts you in the 98th percentile around here.

---

