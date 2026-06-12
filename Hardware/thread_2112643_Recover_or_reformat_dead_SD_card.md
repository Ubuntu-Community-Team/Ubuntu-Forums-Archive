---
title: "Recover or reformat dead SD card"
date: 2013-02-05
forum: Hardware
---

### Post by Mogen317 on 2013-02-05
Hi, I have a SD card that suddenly stopped working.  It's not mounted and isn't even seen on a few computers I've tried.  In Ubuntu there's no change in the devices in /dev.

Any one have any ideas about how to recover my data from the SD card or even how to wipe it and reformat it?  I've found a bunch of guide on how to recover files from an SD card and how to reformat external drives but nothing that deals with a external drive that can't been seen or mounted.

Thanks!

---

### Post by Cheesemill on 2013-02-05
If nothing is even detecting the drive then I would say it is probably dead.

Can you post the output of ...
```
dmesg | tail -n 20
```
shortly after plugging the SD card into your machine.

---

### Post by Mogen317 on 2013-02-05
Output of dmesg | tail -n 20

```

[10588.135764] sd 4:0:0:0: [sdc] No Caching mode page present
[10588.135772] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[10588.138064] sd 4:0:0:0: [sdc] No Caching mode page present
[10588.138071] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[10588.139583]  sdc: sdc1
[10588.140737] sd 4:0:0:0: [sdc] No Caching mode page present
[10588.140739] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[10588.140741] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[10770.720174] sdc: detected capacity change from 7969177600 to 0
[10772.562762] usb 3-2: USB disconnect, device number 2
[10802.563352] mmc0: error -110 whilst initialising SD card
[10802.648759] mmc0: error -110 whilst initialising SD card
[10802.730947] mmc0: error -110 whilst initialising SD card
[10802.811075] mmc0: error -110 whilst initialising SD card
[10802.891341] mmc0: error -110 whilst initialising SD card
[10802.980080] mmc0: error -110 whilst initialising SD card
[11909.291500] mmc0: error -110 whilst initialising SD card
[11909.372214] mmc0: error -110 whilst initialising SD card
[11909.451843] mmc0: error -110 whilst initialising SD card
[11909.536735] mmc0: error -110 whilst initialising SD card

```

sdc: sdc1 looks hopeful.  Maybe I missed that in /dev before.

---

### Post by Cheesemill on 2013-02-05
The message from sdc was for an event that happened about 20 minutes ago (the first set of numbers in the dmesg output is seconds since boot).

The mmc errors seem to back up my suggestion that the card is completely dead.

---

### Post by Mogen317 on 2013-02-05
My usb flash drive must have been sdc.

And that is unfortunate.  Perhaps the super cheap Amazon Basics SD cards aren't as great as I thought.

---

