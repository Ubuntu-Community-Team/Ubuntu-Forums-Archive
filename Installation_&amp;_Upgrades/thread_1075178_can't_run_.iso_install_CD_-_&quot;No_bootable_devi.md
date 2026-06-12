---
title: "can't run .iso install CD - &quot;No bootable devices&quot;"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by TimDaniels on 2009-02-20
I'm trying to re-install Ubuntu with version 8.04.2 on a laptop with Vista installed.  The Vista/Ubuntu dual-boot worked fine until I removed the Ubuntu kernel.  The .iso file's MD5 hash checks out on the CD under Vista, and the boot sequence on my laptop is set with 1) CD, 2) USB, 3) internal hard drive.  But the error msg "No bootable devices - ...." appears after POST.  The name of the .iso file is "ubuntu-8.04.2-desktop-i386.iso", and the CD drive is able to read the file well enough to calculate its MD5 hash value.  Why won't the laptop boot from the Ubuntu installation CD?  What am I missing?

*TimDaniels*

---

### Post by AliTabuger7 on 2009-02-20
Did you burn the iso file itself to the disk? If you look at the disk in explorer and it has a .iso file on it, that is incorrect.

Read more here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by TimDaniels on 2009-02-20
That was it!  I used ISOrecorder to copy the .iso file to the CD, and now the CD boots up with to run the installer.  Thanks muchly.

*TimDaniels*

---

