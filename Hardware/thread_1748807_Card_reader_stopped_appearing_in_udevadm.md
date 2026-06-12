---
title: "Card reader /stopped/ appearing in udevadm"
date: 2011-05-03
forum: Hardware
---

### Post by tbridges42 on 2011-05-03
I'm finally getting the hang of udev, and having successfully used it to automount my cd-rom and flash drive, I moved on to my cf card reader. At one point I got fed up and rebooted. After my reboot, udevadm --monitor stopped showing any events associated with my card reader at all. I have no idea why, so I undid all the changes I had made, and it still doesn't show up. I tried installing udisks, even though I shouldn't have to, since it was working literally half an hour ago, and it worked exactly once. I installed it, it displayed one event the next time I plugged in a card, and nada since. Udev still sees it, because I can still mount it from /dev/sdc1, but no matter what I do, no events appear.

Recap: put card in, event; removed card, event; reboot computer, no more events ever.

Any ideas?

---

### Post by tbridges42 on 2011-05-04
Approximately 3-4 reboots later, it suddenly started working again. Whatever. If it's still working in a few days, I'll mark this solved, for lack of a [Whatever] tag

---

### Post by tbridges42 on 2011-05-04
That lasted all of 15 minutes. Same deal as before.

---

