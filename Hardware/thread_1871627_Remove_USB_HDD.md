---
title: "Remove USB HDD"
date: 2011-10-29
forum: Hardware
---

### Post by PAleksandrov on 2011-10-29
How to safely remove USB hard disk drive? Is it necessary to turn off a HDD? Earlier it was possible to write 'off' to 'power/level' in sysfs. As I have understand, now it is not possible. When I write '1' to 'remove' in sysfs ('bus/usb/...'), the indicator on the HDD turns off, but the disk continues rotating (I hear the sound when I bring the HDD to my hear). Commands 'hdparm -yY /dev/sdf', 'eject /dev/sdf' and 'eject -s /dev/sdf' doesn't make the disk stop rotating.
OS: Kubuntu 11.10.

---

### Post by haqking on 2011-10-29
> **PAleksandrov said:**
> How to safely remove USB hard disk drive? Is it necessary to turn off a HDD? Earlier it was possible to write 'off' to 'power/level' in sysfs. As I have understand, now it is not possible. When I write '1' to 'remove' in sysfs ('bus/usb/...'), the indicator on the HDD turns off, but the disk continues rotating (I hear the sound when I bring the HDD to my hear). Commands 'hdparm -yY /dev/sdf', 'eject /dev/sdf' and 'eject -s /dev/sdf' doesn't make the disk stop rotating.
OS: Kubuntu 11.10.

eject or umount (safely remove option)

USB drives tend to cache before a final write so just unplugging can result in corruption

---

### Post by PAleksandrov on 2011-10-29
> **haqking said:**
> eject or umount (safely remove option)

USB drives tend to cache before a final write so just unplugging can result in corruption

Does umount command has a special safely remove option?
Unmounting doesn't make the disk stop rotating? Is it safe to physically unplug the HDD cable from USB port when the disk is rotating (even when all partitions on the disk are unmounted)?

---

