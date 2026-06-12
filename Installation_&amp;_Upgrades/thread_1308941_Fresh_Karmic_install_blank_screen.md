---
title: "Fresh Karmic install blank screen"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by muhsim on 2009-11-01
I am unable to boot after fresh install of Karmic Koala 64bit on ASUS UX50V.
The screen goes all blank. If recovery mode is used, the following error appears:

```
[3.790262] [drm] LVDS-8: set mode 1366x768 e
[3.855973] Console: switching to colour frame buffer device 170x48
```And then, after about 5 min the following error shows:
```

/sys/devices/pci0000:00/0000:00:02.0/drm/card0
/sys/devices/pci0000:00/0000:00:02.0/drm/card0
/sys/devices/pci0000:00/0000:00:02.0/drm/card0
(many times with numbers appended to the end) 

Begin: Loading essential drivers...
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system...
 

Waiting for root file system...
/sys/devices/pci0000:00/0000:00:02.0/drm/card0
/sys/devices/pci0000:00/0000:00:02.0/drm/card0
/sys/devices/pci0000:00/0000:00:02.0/drm/card0
(many times with numbers appended to the end) 

```

---

### Post by wilee-nilee on 2009-11-01
Did you try a update from the command line.

---

### Post by muhsim on 2009-11-01
How do I get into command line if even recovery option does not boot?
Do I have to pass some additional arguments during boot-up?
BTW, Live CD stops booting into demo mode after karmic is installed, it only does if I remove all partitions and create a blank partition.

---

### Post by muhsim on 2009-11-01
Fixed by passing the following arguments at boot. Press "E" while on boot menu and then for boot options, add[FONT=Verdana] "[/FONT]i915.modeset=0" (comes after "ro")

This is a critical issue with KMS and needs to be addressed immediately!

---

### Post by muhsim on 2009-11-01
To permanently disable KMS edit /boot/grub/grub.cfg and add the "i915.modeset=0" option to boot parameters. Should be on the line where it says 
> linux /boot/vmlinuz-2.6.... ro quiet splash.
So, it becomes:
> linux /boot/vmlinuz-2.6.. ro quiet splash i915.modeset=0 .

---

### Post by lyc1 on 2009-11-03
Did you report this as a bug in launchpad ?

I have the same problem on the same laptop (UX50V), but your fix doesn't work for me.
Even if I add i915.modeset=1, startup hangs after 3 or 4 seconds...

---

### Post by muhsim on 2009-11-03
> **lyc1 said:**
> Did you report this as a bug in launchpad ?

I have the same problem on the same laptop (UX50V), but your fix doesn't work for me.
Even if I add i915.modeset=1, startup hangs after 3 or 4 seconds...

It should be "i915.modeset=0". Or just "nomodeset".

---

### Post by lyc1 on 2009-11-05
> **muhsim said:**
> It should be "i915.modeset=0". Or just "nomodeset".
:confused:
Why have I read =1 instead of =0 ???

I'm affected by early alzheimer :)

Thanks a lot, I will try again.

---

