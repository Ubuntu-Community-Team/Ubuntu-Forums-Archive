---
title: "Ubuntu Core on DragonBoard 410c eMMC"
date: 2017-04-10
forum: Hardware
---

### Post by ioberry on 2017-04-10
I'm trying to run Ubuntu Core on [DragonBoard 410c]("https://developer.qualcomm.com/hardware/dragonboard-410c"). There is no problem with running on a microSD card if you use [the official image]("https://developer.ubuntu.com/core/get-started/dragonboard-410c"). But if you write the same image to the built-in eMMC using dd of = /dev/mmcblk0 bs = 10M - the board does not load at all.

How to me explained u[FONT=Helvetica]buntu core has a bunch of dependencies on the bootloader and the partition table to support the following Ubuntu core features:[/FONT]
[LIST]
[*][FONT=Helvetica]rolling back to previous image when upgrade failed[/FONT]
[*][FONT=Helvetica]full system upgrade[/FONT]
[*][FONT=Helvetica]Ubuntu core also uses its own partition table , so i will need to create the partition table on eMMC[/FONT]
[/LIST]
[FONT=Helvetica]
[/FONT]Has anyone tried to do this?[FONT=Helvetica]

[/FONT]

---

