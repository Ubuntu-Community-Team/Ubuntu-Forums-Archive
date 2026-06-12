---
title: "[SOLVED] SD card not mounting"
date: 2008-11-12
forum: Hardware
---

### Post by AZorin on 2008-11-12
Hi, Ive got a problem with an SD card that I have (it used to work with Ubuntu) but now it won't mount (It still works in Windows). Whenever I try to mount it, it quickly (For about a few milliseconds) shows it as a device (I did that in Nautilus). Just yesterday it worked and then today it just didn't work. Can someone plz help me

---

### Post by AZorin on 2008-11-19
Just had to repartition it:KS

---

### Post by dabl on 2008-11-19
SD cards are normally formatted FAT32.  It is not the world's most robust filesystem format, and if you yank it out of the card reader before your system has finished writing data to it, you'll corrupt it.

If the data that you put on it is transitory and easily replaced, then sticking it in a Windows box and reformatting it every other week is quick and easy.

If the data is important and you can't afford to have it trashed, you might consider a more robust filesystem -- NTFS if it has to be shared with Windows, or ext2 if it is Linux only.  Note that it is very important that you use "eject" or "safely remove" prior to pulling it out of the card reader -- that tells the system to flush any remaining writes to the device before it is removed.  :)

---

