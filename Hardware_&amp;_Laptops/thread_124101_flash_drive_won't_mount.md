---
title: "flash drive won't mount"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by VitaminG on 2006-01-31
I just did a fresh install of ubuntu, and now my flash drive won't mount. When I do it through the file browser, it gives an error message reading "given UDI is not a mountable volume." If I try to use mount or pmount, it claims that the device cannot be found in /etc/fstab or /etc/mtab. I tried adding a reference to the drive(/dev/sda) to both, and that just changed the error message to(given device is currently busy.) I haven't found any other ideas of how to get it to work, and I have thoroughly searched the wiki and forums. If you have any ideas, please help me, I need this drive to transfer my modem drivers to linux, and i'm not willing to waste a dvd on one 900k driver.

If it will help, the drive ia an A-Data PD2 MyFlash drive, 512MB. I have tried formatting it to FAT, FAT32, and NTFS, it hasn't helped at all.

---

### Post by VitaminG on 2006-01-31
Solved, I formatted my HD and the flash drive in Knoppix(best LiveCD available), then reinstalled ubuntu and formatted both drives in the built-in partitioner. Now both are working great, the flash drive even works on windows yet, though I'm planning on completely dumping windows soon.

---

