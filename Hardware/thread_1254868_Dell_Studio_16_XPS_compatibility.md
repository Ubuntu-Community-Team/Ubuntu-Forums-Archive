---
title: "Dell Studio 16 XPS compatibility"
date: 2009-08-31
forum: Hardware
---

### Post by cos85 on 2009-08-31
It looks deceptively perfect:
Intel wireless, supported ATI graphics... 
but has anyone tried Linux on it?

The spec lies herein:
[http://www1.euro.dell.com/uk/en/home/Laptops/laptop-studio-xps-16/pd.aspx?refid=laptop-studio-xps-16&s=dhs&cs=ukdhs1](http://www1.euro.dell.com/uk/en/home/Laptops/laptop-studio-xps-16/pd.aspx?refid=laptop-studio-xps-16&s=dhs&cs=ukdhs1)

Any advice greatly appreciated! :)

---

### Post by rrplay on 2009-08-31
you might want to check this out:  [http://www.linlap.com/wiki/dell+studio+xps+16]("http://www.linlap.com/wiki/dell+studio+xps+16")

---

### Post by cos85 on 2009-09-01
Thanks rrplay. It looks like the hardware config has changed since they updated that wiki. It now has an ATI Mobility RADEON HD 4670 instead of an HD 3670 (and perhaps it will now work properly).

I'm a bit concerned about the touchpad not working after suspend, though. 

Does anyone else have a laptop from this range that may be able to clear this out?

---

### Post by Chilly_Willy on 2009-10-10
I use it with Karmic. Standy resume in de default configuration works once.

I edited /etc/default/acpi-support and commented out the following lines:
```

# Should we save and restore state using the VESA BIOS Extensions?
#SAVE_VBE_STATE=true

# The file that we use to save the vbestate
#VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true

```

shutdown and reboot doens't work either. So I have to keep the power button pressed to shutdown.

Other then that it works perfectly.

---

### Post by rrplay on 2009-10-10
Chilly_Willy>> try to overview your ATI driver install process.. maybe take a look here at this thread [http://ubuntuforums.org/showthread.php?p=7996934#post7996934]("http://ubuntuforums.org/showthread.php?p=7996934#post7996934") && redit /etc/default/acpi-support 
to it's org default before checking out the ATI install methods posted.

---

