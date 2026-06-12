---
title: "cdrom_pc_intr on Acer TravelMate 522TX"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by shufla on 2005-10-14
Hello,

Situation: fresh & default install of Breezy Release on my laptop.
I've used kernel option `irqpoll' to make my lap workable.
After putting some big (over 500MB) files via FTP (vsftpd) to my $HOME laptop started to drive crazy with such lines (repeated at maximum speed on console):

hdx: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

(hdx=hdc)

More info: all network interfaces are down, keyboard unusable.

That laptop is in 100% hardware good (all runs fine on Sarge with kernel 2.6, and that files are accessible from my PLD rescue CD with kernel 2.4).

I've deleted that files, and now all runs fine.

Any suggestions?

Best Regards,
Luke

---

