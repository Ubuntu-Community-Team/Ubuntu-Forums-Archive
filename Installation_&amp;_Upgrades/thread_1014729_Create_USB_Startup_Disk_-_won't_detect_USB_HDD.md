---
title: "Create USB Startup Disk - won't detect USB HDD"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by bretto_40 on 2008-12-18
I have a 80gb external USB HDD and I want to install a persistent copy of Ubuntu 8.10 onto it, which as I understand should be simple to do using the USB start up disk utility.

No matter what I try whenever I start the USB startup disk it will not detect my USB HDD in the list of available USB devices.

I have even gone as far as completely reformatting the entire disk and making it a FAT32 disk, (even tried unformatted) and no success.

The only other unknown factor is that previously with this disk I tried using Unetbootin once to install a previous copy of Ubuntu on it. Could it be that Unetbootin did something to the MBR of the disk that is causing this behaviour? I would have thought the MBR gets reformatted with the disk?

Note: I can access the HDD no probs and can use Nautilus to browse it etc. And yes, I have tried it both mounted, and unmounted.

Does anyone have any suggestions as to what might be my problem here?

I have a 4gb USB key that gets detected by the create USB start up disk program no probs..... it just will not detect my USB HDD... HELP!  ](*,)

---

### Post by bluegizmo83 on 2008-12-24
I'm having the same issue. I can create a live usb disk on a FLASH memory stick just fine, but it will not detect my usb HDD (2.5" 40gb in a rocketfish enclosure). Ubuntu detects it and mounts it just fine, but the usb-creator will not see it. I have tried mirroring the partition of the flash stick, deleting the partion, ect. I have even tried installing the live usb on the flash stick and then doing a mirror image copy from the flash to the usb hdd. Come on Guru's, helps us little guys out!

---

### Post by snivek on 2008-12-29
bump

---

### Post by bluegizmo83 on 2009-01-04
bump

---

### Post by Old_Grey_Wolf on 2009-01-04
I noticed that the applications says "Please insert an USB **stick**". Bold type is mine. I don't think it was intended to be used with USB external HDDs.

USB (Universal Serial Bus) is a serial bus standard to interface devices. It does not make a HDD equal to flash memory.

---

