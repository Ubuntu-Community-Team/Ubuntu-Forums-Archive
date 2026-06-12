---
title: "Will ubuntu automatically recognize upgraded 2nd hard drive?"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by rhatch on 2007-09-21
I used to teach c programming, but I'm a total beginner with ubuntu.  I have newly installed and working ubuntu 7.04 installed on an old Dell with two physical hard drives.  Both hard drives are now working.  To make this unit useful, I need to upgrade the second hard drive, the one that does not hold the operating system.  If I simply install an upgraded  hard drive of around 500 GB, will ubuntu automatically recognize it, or do I have to invoke some procedure to get it recognized?

Dick Hatch

---

### Post by jnorthr on 2007-09-21
Welcome aboard ! 

Does ubuntu already 'see' your second drive now ? You may need to change the bios setting to reflect the characteristics of your new drive. You will need to format it as well but i'd just plug it in and see what happens. Then reboot. Ubuntu always re-examines all the hardware at each boot and i would expect that your new hardware would be correctly recognised even if not formatted. You can always use grub to re-partition it. Good luck. :)

---

### Post by rsambuca on 2007-09-21
> **jnorthr said:**
> Welcome aboard ! 

Does ubuntu already 'see' your second drive now ? You may need to change the bios setting to reflect the characteristics of your new drive. You will need to format it as well but i'd just plug it in and see what happens. Then reboot. Ubuntu always re-examines all the hardware at each boot and i would expect that your new hardware would be correctly recognised even if not formatted. You can always use grub to re-partition it. Good luck. :)

You will probably have to add the drive to your /etc/fstab file to have it automounted, and (I assume the above was a typo), you may have to use [COLOR="Red"]gParted[/COLOR] to format/partition it.

---

