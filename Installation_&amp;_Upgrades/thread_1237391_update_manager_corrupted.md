---
title: "update manager corrupted"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by stephenfranklin on 2009-08-11
hi, im new to ubuntu 9.04 i installed it in my system with the live cd.
i updated it using the update manager.
after the update process my update manager is not working properly.
it shows the error like this..

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
 

help me in this problem...

thanks in advance..:P

---

### Post by stephenfranklin on 2009-08-11
i tried in terminal by typing the command
```
 sudo dpkg --configure -a
```

this shows result like this...

```
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-initrd-2.6.24.4-desktop-1mnb.img
Cannot find /lib/modules/initrd-2.6.24.4-desktop-1mnb.img
update-initramfs: failed for /boot/initrd.img-initrd-2.6.24.4-desktop-1mnb.img
dpkg: subprocess post-installation script returned error exit status 1
```

pls....

---

### Post by stephenfranklin on 2009-08-31
hi friends i got a solution from this thread

[http://ubuntuforums.org/showthread.php?p=7217618]("http://ubuntuforums.org/showthread.php?p=7217618")

i had followed this instructions and it works like a charm!

thank u for ur support...

---

### Post by shredder12 on 2009-08-31
> **stephenfranklin said:**
> hi friends i got a solution from this thread

[http://ubuntuforums.org/showthread.php?p=7217618]("http://ubuntuforums.org/showthread.php?p=7217618")

i had followed this instructions and it works like a charm!

thank u for ur support...

Its good that the problem is solved.. but isn't it a temporary fix..
Is there a proper way to fix this problem??

---

