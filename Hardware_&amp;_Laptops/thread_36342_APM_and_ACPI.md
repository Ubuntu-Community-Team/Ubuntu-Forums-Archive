---
title: "APM and ACPI"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by Arthemys on 2005-05-23
I've finally got my new IBM ThinkPad R51 and have most of the hardware working the way I want. I recently enabled APM as per suggestion by my fiance, however I am not able to utilize a number of options my BIOS supports. So I tried enabling ACPI at the same time, everything worked like a charm, suspend and the other features worked.
(Suspend worked under APM only just fine)

Now having both enabled PREVENTS suspend from working, and ACPI alone won't suspend. I've made NO changes to anything regarding power in the OS or BIOS. All the other functions, such as wireless on/off and drive bay swapping run fine with APM and ACPI, just not suspend.

Also, if possible I'd like to only enable ACPI because I've been informed APM is old and needs to be depricated.

Is this something anyone else knows about?

---

### Post by shof2k on 2005-05-23
Is it as simple as adding in a boot parameter (apm=off) or removing the module from the kernel?  I'm sure ACPI does more than what's expected.  If I boot with ACPI off, I get better cpu control but no sound.  

good luck

---

### Post by Arthemys on 2005-05-23
I just change the boot parameters to switch them around.

---

