---
title: "intrepid not booting no grub menu after fresh install"
date: 2008-11-03
forum: General Help
---

### Post by Smendrick on 2008-11-03
right basically after a complete fresh install on my linux drive basically ubuntu wont boot, and neither is the grub menu loading!!! basically my pc is just booting into windows!!!

---

### Post by meierfra. on 2008-11-03
Try switching the boot order in the bios.

---

### Post by dcstar on 2008-11-03
> **Smendrick said:**
> right basically after a complete fresh install on my linux drive basically ubuntu wont boot, and neither is the grub menu loading!!! basically my pc is just booting into windows!!!

I have found the default location for the Grub boot loader (hd0) is not correct for a lot of configurations. I had to do a re-install after suffering the same symptoms as you and select "sd0" manually from that last phase of the install process.

You  may want to do a forum search for "reinstall grub" and follow those instructions, it could well fix your issue quickly.

---

