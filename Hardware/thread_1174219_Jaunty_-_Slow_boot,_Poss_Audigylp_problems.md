---
title: "Jaunty - Slow boot, Poss Audigy/lp problems?"
date: 2009-05-30
forum: Hardware
---

### Post by russ_armst on 2009-05-30
[SIZE=1][SIZE=1]Hi all,
Since upgrading to Jaunty (AMD64) I've been experiencing very slow boot times (>2mins). dmesg revealed:

[   17.872665] EMU10K1_Audigy 0000:01:0b.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   17.874989] Audigy2 value: Special config.
[  107.391654] lp: driver loaded but no devices found
[  107.410741] it87: Found IT8712F chip at 0x290, revision 7[/SIZE]

Note the 90 second difference between the 'Audigy2 value' line and the next. This is on a clean install. Googling has revealed nothing. Can anyone point me in the right direction?

Thanks

Russ.
[/SIZE]

---

### Post by Greensystemsgo on 2009-05-30
How much Ram do you have? im assuming its a x64 processor...

any reason the change from x32 to x64? go back to x32?

---

