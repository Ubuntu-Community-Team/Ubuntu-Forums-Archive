---
title: "Live CD (v 5.10) freezes on &quot;Starting hotplug subsystem...&quot;"
date: 2005-11-24
forum: General Help
---

### Post by yongqli on 2005-11-24
The computer hangs while booting from the LiveCD v 5.10 while on "Starting hotplug subsystem...". Any help appreciated.

---

### Post by aysiu on 2005-11-24
Did you [do a checksum on the ISO image before burning it](http://www.linuxiso.org/viewdoc.php/verifyiso.html) or burn at a slow speed?

---

### Post by blunt on 2005-11-29
i have the same problem, and i have an original ubuntu cd. 

on my laptop, when i try to load the live cd, the system just freezes on the "Starting hotplug subsystem". is there any boot option that i should try? 

thanks in advance.

---

### Post by zayenz on 2005-11-30
I have experienced the same problem when trying to boot up an LG LW20 notebook using the Breezy Live CD. Pressing CTL-C does not work, nothing happens. There are no external devices plugged in, so I can't unplug anything either. 

If somebody has any good ideas, I'm interested in hearing them

/Zayenz

---

### Post by thedstro on 2005-12-02
I had the same problem! In my case disabling the on-board sound through the BIOS setup fixed it and allowed me to boot. This is just a workaround of course! The solution could be replacing the sound driver (intel_snd_hda I think it was called in my case) or changing to udev instead of hotplug.

---

