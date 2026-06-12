---
title: "Trying to get grub to allow 3 os boot"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by wpsmithii on 2009-10-31
I've had XP pro and ubuntu as a dual boot and I just upgraded to 9.10 (it went perfectly) and added a 40 gig hdd to put CAElinux on I've got the install done and I ran "sudo grub-mkconfig -o /boot/grub/grub.cfg" in 9.10. It found the 3 os's ie, 9.10, XP pro. and PCLinux OS.
last 2 lines of output;
Found PCLinuxOS release 2007 (PCLinuxOS) for i586 on /dev/sdb1

grub-probe:error: Cannot find a GRUB drive for /dev/sdb1. Check your device.map. 

I'm a noob, what does this mean and how do I fix it?

---

### Post by cariboo on 2009-10-31
All you should have to do is run:

```
sudo grub-update
```

and it should find your other oses.

---

### Post by wpsmithii on 2009-11-01
When I ran sudo grub-update the feedback is "command not found" I think from my research that we're dealing with grub 2 in 9.10. Bill

---

