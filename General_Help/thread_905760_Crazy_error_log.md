---
title: "Crazy error log"
date: 2008-08-30
forum: General Help
---

### Post by Pixel on 2008-08-30
I noticed every time I shut down or reboot when the screen goes back into console mode, the screen is flooded with errors that go by so fast i can't really read them or figure out why they're happening.

So I was looking through my logs in /var/logs and found a file called kern.log.0,  It was 21 mb, which was noticeably larger than any of my other logs so far (it's a fresh install, only a few days old).

```
Aug 30 06:08:52 homebox kernel: [117808.816257] phy0 -> rt2500pci_bbp_write: Error - BBPCSR register busy. Write failed.
Aug 30 06:08:52 homebox kernel: [117808.816761] phy0 -> rt2500pci_bbp_write: Error - BBPCSR register busy. Write failed.
Aug 30 06:08:52 homebox kernel: [117808.817271] phy0 -> rt2500pci_bbp_write: Error - BBPCSR register busy. Write failed.
Aug 30 06:08:52 homebox kernel: [117808.817782] phy0 -> rt2500pci_bbp_write: Error - BBPCSR register busy. Write failed.
Aug 30 06:08:52 homebox kernel: [117808.874142] phy0 -> rt2500pci_rf_write: Error - RFCSR register busy. Write failed.
Aug 30 06:08:52 homebox kernel: [117808.874647] phy0 -> rt2500pci_rf_write: Error - RFCSR register busy. Write failed.
Aug 30 06:08:52 homebox kernel: [117808.875151] phy0 -> rt2500pci_rf_write: Error - RFCSR register busy. Write failed.
```It just says this over and over and over, though I'm not sure if this was the same message i was getting in the console when i rebooted or not, i'd still like to fix this, because given a few more days the log oculd easily go over 100mb and eat up my precious hdd space...

Any clue what to do to stop this?

---

### Post by Pixel on 2008-08-30
Ok well I figured it out, it was a bad driver/driver error for my wireless card, but since i never use it I jsut removed the card from my computer and the errors stopped.

---

