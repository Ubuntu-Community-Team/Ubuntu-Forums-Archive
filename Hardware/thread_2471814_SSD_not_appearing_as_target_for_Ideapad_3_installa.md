---
title: "SSD not appearing as target for Ideapad 3 installation"
date: 2022-02-10
forum: Hardware
---

### Post by newholm1 on 2022-02-10
Hi! I've just bought a Lenovo Ideapad 3 with the intention of running Windows  and Ubuntu in dual boot. I have accessed the bios, told it to boot from  my USB stick, and all seems well until I get to the Partition settings  page. To my dismay, my internal SSD is not listed - only the USB stick  itself. This is true even after shrinking the Windows partition on the  SSD. It seems like the SSD has not powered up or been read by Systemback  at this stage. Can anyone suggest how I can get round this?

Thanks!

Donald

---

### Post by Bashing-om on 2022-02-10
newholm1; Hello

From Windows system insure that the Windows system is fully shut down; ubuntu will not interfere with Windows when the drive is in a "hibernated" state.

[INDENT]a most likely condition
[/INDENT]

---

### Post by oldfred on 2022-02-10
Also make sure you have AHCI drivers in Windows and change in UEFI settings from RAID or Intel RST to AHCI.

Lenovo Ideapad 3 15 with Ryzen 5 5500U Ubuntu 21.04 with the Linux 5.11 kernel, it's been working out fine.
[https://www.phoronix.com/scan.php?page=article&item=lenovo-ryzen5-5500u&num=1](https://www.phoronix.com/scan.php?page=article&item=lenovo-ryzen5-5500u&num=1)

Even if not your model best to have latest UEFI firmware.
UEFI update required for USB-C port issues 2017 thru 2019 models

Some Lenovo models have this setting.
Lenovo Active Protection System&#8482; &#8211; for hard drive
Or this:
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series

---

