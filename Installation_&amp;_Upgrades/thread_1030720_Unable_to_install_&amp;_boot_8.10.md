---
title: "Unable to install &amp; boot 8.10"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by flw on 2009-01-04
I'm attempting to upgrade my FreeNAS server to Ubuntu 8.10.  I can boot on the ISO CD, and run the installation option, apparently successfully.  When it tells me to remove the CD and reboot, however, Ubuntu comes up and gives me a userid/passwd prompt, then goes to a yellow screen with nothing on it.  The mouse moves the cursor, but no clicking, typing, or other input produces any sort of reaction from Ubuntu.  You might call it the yellow screen of death.  What's going on?

H/W:
Older Dell Dimension 2400, 2.2GHz processor, 2GB RAM, 1 40GB HD (boot drive) & 1 250GB HD.

---

### Post by Pumalite on 2009-01-04
Burn a new CD. That's a bad burn.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by flw on 2009-01-04
Ok.  I double-checked the MD5 hash on the .ISO file, then burned another CD.  Copying the contents of both CDs back to my hard drive as ISO files, I compared the MD5 hashes of each.  The two CDs match each other, but are both different than the original ISO file.  Not sure what to think about that.

Instead of loading off a CD again, I GRUB'ed into recovery mode, and did the 'Package Recovery' option on the menu.  After updating something close to 250 packages, it now boots properly and appears to be running well.  

Thanks for your help!

---

