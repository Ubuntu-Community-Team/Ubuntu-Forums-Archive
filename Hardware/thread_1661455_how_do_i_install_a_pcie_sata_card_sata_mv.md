---
title: "how do i install a pcie sata card? sata_mv?"
date: 2011-01-06
forum: Hardware
---

### Post by sixteenornumber on 2011-01-06
im not new to linux but its only recently (about a week) that i've  really taken a dive into it (using more than cd and ls etc).   I didn't have enough SATA ports so I  bought a soft raid card. Spicifically, the card Rosewill RC-218 with a Marvell 88SX7042 chipset.  How exactly would I use this? Im using Ubuntu 10.10 right now. Egg review says,

     Quote:
                                                 *...Works just fine in Linux using the sata_mv driver in the 2.6.26 kernel...                                 *

I tried,

[I]sudo modprove sata_mv
[/I]

I dont really know what to do next. still learning here.

---

### Post by Fafler on 2011-01-07
```
dmesg | egrep -i "SATA|sd"
```

And see if whatever you connected to it shows up. It should.

---

