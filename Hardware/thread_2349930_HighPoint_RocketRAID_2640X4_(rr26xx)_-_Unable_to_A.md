---
title: "HighPoint RocketRAID 2640X4 (rr26xx) - Unable to Access Array"
date: 2017-01-19
forum: Hardware
---

### Post by prcm311 on 2017-01-19
I have been using the 2640X4 for a RAID 5 array for several years now.  I have successfully rebuilt the driver several times as kernel updates have been released.  Recently, I decided to upgrade the CPU in this machine and re-install Ubuntu for a fresh start.  Currently, I have 16.04 (kernel 4.4.0-21) installed.  I have followed this [guide]("https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver") to assist with the install on the 4.4 kernel.  (It may be worth noting that while I'm not a Linux expert I successfully made edits to the source myself to make this work previously.)  The guide calls for using dkms so the driver can be automatically rebuilt when the kernel is updated.  Everything goes smoothly until "sudo modprobe rr26xx" hangs.

I have also tried to make the driver without using dkms.  In both cases "modprobe" appears to hang.  Opening a second terminal and running "lsmod" displays "rr26xx" as running however, the array is not accessible and not listed under "lsblk" or "fdisk."

Any help would be greatly appreciated.  I can provide as many details as required.

---

### Post by prcm311 on 2017-01-30
Resolved by replacing the RAID card.  I ordered a replacement 2640x4 and the array was recognized.  I didn't have to reinstall the driver either, the problem was entirely hardware.  The guide I reference above is excellent; follow the README in the download.

---

