---
title: "corrupted grub configuration"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by stinkyfoot on 2009-08-01
I have somehow messed up my /boot/grub directory. Most recently, I've run Super Grub Disk, which told me that my stage 1 and stage 2 were corrupted or swapped. Attempting to boot from the disk produces the message, "GRUB Hard Disk Error". 

If you can recommend a manual solution, please do so. I have previously tried various parameters to grub and grub-install, but if you're an expert and think you can attempt something with these, please suggest something. Otherwise, could I use the Ubuntu installation DVD? I read a post on launchpad.net that it is possible to use the final option when choosing the partitions to install to; Ubuntu will try not to overwrite non-system files. Is this true?

Thanks.

EDIT: I previously wrote that the error message was "GRUB Hard Drive Error". That appears not to have been the case judging by posts elsewhere online.

EDIT: I have Ubuntu on another disk that works just fine on the same motherboard and BIOS.

---

### Post by mikewhatever on 2009-08-01
Have you tried reinstalling GRUB with the Super Grub disk?

---

### Post by stinkyfoot on 2009-08-01
I believe that I tried every option it offered.

---

### Post by stinkyfoot on 2009-08-02
Using the last option as I suggested, the Ubuntu installation CD attempted to overwrite simply the system files. It got to "grub-install (hd0)" and failed, so installation was aborted.

---

