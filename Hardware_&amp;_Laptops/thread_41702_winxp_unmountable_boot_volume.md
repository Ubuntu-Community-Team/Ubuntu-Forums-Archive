---
title: "winxp: unmountable_boot_volume"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by kermy on 2005-06-14
After installing ubuntu I get a blue screen error from Windows XP upon booting: UNMOUNTABLE_BOOT_VOLUME.

What gives?

Ubuntu overwrites the PSA (secret partitions) of my R50p IBM laptop and this kills windows xp for some reason. Does anybody know how to fix this? I had to order cds from IBM to recover my Windows XP, but after installing Ubuntu it got corrupted again, doh.. Warty did not do the same, it didn't even see the space that the PSA used.

---

### Post by electrosoccertux on 2005-06-14
Hmm...whats your boot.ini file say? If windows is partition 2 (it will say 2, not 1, 1 is first unlike linux partions where 0 is first), and ubuntu is first, but windows thinks it is first, then when you select windows, the windows boot loader would be trying to boot your ubuntu partition.

Maybe changing the partition number in boot.ini (hidden file on c:) would help. Prolly not, but hopefully so.

---

### Post by kermy on 2005-06-14
[QUOTE=electrosoccertux]
Maybe changing the partition number in boot.ini (hidden file on c:) would help. Prolly not, but hopefully so.[/QUOTE]

The boot.ini has not been changed. I use grub as a boot loader.

---

