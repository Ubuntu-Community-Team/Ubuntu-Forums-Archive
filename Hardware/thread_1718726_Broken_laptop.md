---
title: "Broken laptop"
date: 2011-03-31
forum: Hardware
---

### Post by surfingonmusic on 2011-03-31
ok so my acer aspire one which runs xp would randomly decide not to boot up when i turned it on. One day it just refused to boot into windows. i had a live linux (ubuntu netbook) usb so i put that on it and installed it as a dual boot. it worked for a few days but then i got this error whenever i turned it on

error unknown partition
grub rescue

i got an xp live cd to go into the recovery console but even there it wasn't able to see the hard drive.
did installing linux do this? or is it a hardware problem

---

### Post by Dutch70 on 2011-03-31
From what little info we have to go by here, it sounds like your hard drive may be failing, but I certainly wouldn't assume the worst.

Can you boot up the live cd/usb with Ubuntu on it? We could probably get a lot more info from that.

If you can, open Disk Utility (System>>Admin>>Disk Utility) Click your hdd on the left and run a SMART data check on it.

---

### Post by surfingonmusic on 2011-04-10
it's fixed! the bootloader was ****** and the install disk didn't have any SATA drivers...all good now did a 'fix mbr' in the recovery console thanks for the help!

---

