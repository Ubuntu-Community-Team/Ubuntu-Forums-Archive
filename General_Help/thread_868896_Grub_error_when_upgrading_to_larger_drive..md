---
title: "Grub error when upgrading to larger drive."
date: 2008-07-24
forum: General Help
---

### Post by fade2gray on 2008-07-24
This has been my setup while experimenting with Ubuntu 8.04 server edition.

hda1 40G: Installation.
hdb1 40G: For PING images, file system backups etc.

I tried swapping hda1 for a 150G drive (all are basic IDE drives) and restored a known working PING image. Rebooting after restore results in "LOAD ERROR! - Press any key to reboot", pressing any key reboots the machine which then continues load with any further problems. Rebooting, after a successful login, repeats the cycle.

After logging in, I tried ...

sudo grub
> root (hd0,0)
> setup (hd0)
> exit

... which didn't solve anything.

I tried a clean install on the 150G drive which resulted in the same problem.

Any advice please?

---

### Post by Potatoj316 on 2008-07-24
did you make sure the jumpers on the drives are in the correct place?  It dosent really sound like thats the problem though because it works every other time (am I reading that right?)

---

### Post by fade2gray on 2008-07-24
Nope, the 150G Hitachi drive just won't have Ubuntu server running on it, but it mounts quite nicely as an extra data drive and I've reverted back to the 40G for the main installation.

In hindsight though, I believe that when I had the 150G running on a windows machine I may have had Norton GoBack installed at the time - I think GoBack can do strange things to the boot sector.

---

