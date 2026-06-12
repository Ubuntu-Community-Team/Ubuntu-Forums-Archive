---
title: "No CD/DVD Writer detected."
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by hellmet on 2007-09-20
I recently got myself a Dell 1520 lappy. I installed using the CDRom , and now I tried to write a cd, when I discovered that my CD/DVD Writer was not detected at all !! Does any one have any idea what the problem could be?

Fstab has this ::

/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

so the cd drive MUST have been detected initially. Now, mount /dev/hda, says there's no such device.
lspci doesn't show any Cd Dvd device at all.

It works in Vista, though.

---

### Post by dcstar on 2007-09-20
> **hellmet said:**
> I recently got myself a Dell 1520 lappy. I installed using the CDRom , and now I tried to write a cd, when I discovered that my CD/DVD Writer was not detected at all !! Does any one have any idea what the problem could be?

Fstab has this ::

/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

so the cd drive MUST have been detected initially. Now, mount /dev/hda, says there's no such device.
lspci doesn't show any Cd Dvd device at all.


Why would it?, an IDE device is not a PCI device.

Use **lshw**.

---

### Post by nickcase on 2007-10-20
Exactly the same problem here.  Fresh Feisty install - I have the same fstab entries as above, the CDROM fails to mount - /dev/hda is missing.

How do we fix this?

Thanks

Nick

---

### Post by maclenin on 2007-10-21
I have a similar issue:

1. I put a cd (with digital photos) into my cd/dvd burner.
2. The drive spins up but doesn't seem to mount - no icon appears on the desktop and I cannot navigate to the cd-rom/contents via my file manager.
3. The device is listed in fstab: /dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

4. ...but doesn't seem to mount.....

Any thoughts?

Config: Feisty / HP 6910p / Dual-Layer DVD/CD burner

---

### Post by maclenin on 2007-10-22
Folks:

Give this [_post_]("http://ubuntuforums.org/showpost.php?p=3401551&postcount=5") a look - seems to have solved the CD mount problem for me....

Good luck!

P.S. And though I am Feisty, I imagine it should work for Gutsy, as well....

---

### Post by evil_cat on 2007-10-23
Excellent 


"sudo modprobe ide_generic"

works fine for me :popcorn:

---

### Post by hellmet on 2007-10-25
I returned my Dell for a desktop. Period.

---

