---
title: "Install from USB Drive fails during partition editing"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by FiremothPilot on 2008-12-24
Hey everybody,

I'm trying to install Ubuntu 8.04 LTS on my new Samsung NC-10 netbook.

I used UNetBootIn to prepare the USB drive from an existing disc image I had on my hard drive.

I can successfully boot into the installation environment, but when it comes time to select the destination partition and it's mount point, the dialog hangs when I click 'Forward' after editing the partitions. The little circle thing spins indefinitely. I also notice that, after this point, the access light on the flash drive is no longer working (the installer is no longer accessing the USB drive).

Does anyone know why this is happening or what I can do to circumvent the error?

I've tried different USB drives, a SD card, and about three other ways of doing this...I JUST WANNA INSTALL UBUNTU ON MY NEW TOY!

Please help!

---

### Post by mikewhatever on 2008-12-24
Is this a clean installation on the clean HDD, or are resizing Windows or data partitions?

---

### Post by FiremothPilot on 2008-12-24
> **mikewhatever said:**
> Is this a clean installation on the clean HDD, or are resizing Windows or data partitions?

I have tried to run the install with both a prepared ext3 partition (half of the hdd, with the Recovery partition left alone) and with a full ntfs partition (resize and allocation using the tool within the live installer).

The installer fails in approximately the same stage in both cases.

---

