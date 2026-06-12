---
title: "Booting order not found"
date: 2020-11-30
forum: Hardware
---

### Post by satimis on 2020-11-30
Hi all,

Ubuntu 20.04

I encounter booting problem on adding a new MSI Geforce GTX 1650 Super Display Card

At booting it popup "Booting order not found"

On BIOS
Booting
1st Boot```

UEFI OS Samsung SSD 860 EVO 2TB
```

It can't be saved

On next boot it selects```

Ubuntu SSD 860 EVO 2TB
```
resulting in unable to boot.  

Then I have to rebooting several times to boot up Ubuntu

Where I have to fix this problem.

Thanks

Regards

---

### Post by CelticWarrior on 2020-11-30
You should check you Boot order in UEFI.
Hardware changes sometimes result in the reset of firmware settings.

---

### Post by oldfred on 2020-11-30
Do you have fast boot on in UEFI settings?

Fast boot assumes no hardware or system changes & immediately jumps to booting system. 
A normal boot will rescan system and update settings for operating system to use.
If fast boot on, you may not have time to press correct key to get into UEFI settings as it immediately boots.
Then you usually can do a full "cold" boot or shutdown, unplug from power,  remove battery if laptop, drain system by holding power switch and then boot & press correct key immediately.

Did you install correct driver for new card.
If older card & driver, did you totally purge old driver as new driver will not remove old & then you get conflicts.
If driver not installed you may need nomodeset boot parameter to boot until you install driver or recovery mode boot to terminal mode to install driver.

---

### Post by satimis on 2020-11-30
> **oldfred said:**
> Do you have fast boot on in UEFI settings?

Fast boot assumes no hardware or system changes & immediately jumps to booting system. 
A normal boot will rescan system and update settings for operating system to use.
If fast boot on, you may not have time to press correct key to get into UEFI settings as it immediately boots.
Then you usually can do a full "cold" boot or shutdown, unplug from power,  remove battery if laptop, drain system by holding power switch and then boot & press correct key immediately.

Did you install correct driver for new card.
If older card & driver, did you totally purge old driver as new driver will not remove old & then you get conflicts.
If driver not installed you may need nomodeset boot parameter to boot until you install driver or recovery mode boot to terminal mode to install driver.
Thanks for your advice.  I haven't installed any driver coming with CD

Now on Secure Boot, I select other OS

It seems booting without problem now.  I'll watch a while

Regards

---

