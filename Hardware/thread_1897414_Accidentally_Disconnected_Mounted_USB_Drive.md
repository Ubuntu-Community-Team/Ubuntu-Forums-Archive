---
title: "Accidentally Disconnected Mounted USB Drive"
date: 2011-12-19
forum: Hardware
---

### Post by JamieKitson on 2011-12-19
Hi,

What is the best practice when a mounted (usb) drive is disconnected accidentally while mounted in Linux?

If you don't have physical access to the machine what's the best Linux command to run to clear the disconnected drive(s) from mtab?

Thanks, Jamie

---

### Post by coffeecat on 2011-12-19
I think the system clears mtab automatically. I've just tried plugging in a FAT32 pendrive. It was automounted and appeared in mtab. Then I pulled it out without unmounting it and mtab no longer shows it.

---

