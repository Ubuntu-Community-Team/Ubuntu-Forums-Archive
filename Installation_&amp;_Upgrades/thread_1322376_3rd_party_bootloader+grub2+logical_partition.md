---
title: "3rd party bootloader+grub2+logical partition"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by bdubawoop on 2009-11-10
just curious if anyone's had any luck with this combo yet.

ive tried 3 installs of debian squeeze to 2 diff logical partitions on 2 diff hard drives & 1 install of ubuntu 910 & they all bomb with 'partition is not bootable'.

i finally got squeeze to boot by installing to a primary partition.

i follow the same procedure as my other 7 or 8 installs in the past (with the old grub), installing grub to the root partition & using a 3rd party boot manager to boot (currently BING).

i tried following the procedure to revert back to grub .97 on squeeze but it bombed, maybe ill try it with ubuntu later.

---

### Post by bdubawoop on 2009-11-14
I removed grub2, installed grub .97 & it booted right up.

---

### Post by tbessie on 2009-11-27
> **bdubawoop said:**
> I removed grub2, installed grub .97 & it booted right up.

I was having the same problem (check my posts), and found, indeed, that Grub2 seemed unable to be installed on logical partitions, just primary ones, at least in the setup I have.

I had the luxury of reformatting and using a primary root partition (with my 3rd party boot loader), so that's fine for now, tho' Grub2 has issues, I think.

- Tim

---

