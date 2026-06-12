---
title: "DVD drive will not mount"
date: 2008-09-11
forum: Hardware
---

### Post by capnjim on 2008-09-11
I'm running Mytybuntu 8.04 for my MythTV box. All of a sudden for no reason I can work out my DVD drive (actually a Lite-On Blu-ray/DVD combo) will not mount. Trying to mount it gives me a message that "Special device scd0 does not exist."

The drive works fine as I can boot from it, but under a normal boot it no longer shows up. scd0 does not exist any more, as it says, and it is /dev/scd0 that is referenced in my fstab.

I have checked a number of posts on this forum that refer to similar problems, including issues with acpi and using Grub to turn this off, but to no effect.

I am not that technical - can anyone offer some advice on how I could troubleshoot this? 

Thanks in advance.

---

### Post by capnjim on 2008-09-11
Just discovered that the DVD in the drive was showing in /dev/disk/by-label and I could mount it. However it was not showing in by-uuid (was hoping I could force a mount by UUID), so still cannot auto-mount.

---

