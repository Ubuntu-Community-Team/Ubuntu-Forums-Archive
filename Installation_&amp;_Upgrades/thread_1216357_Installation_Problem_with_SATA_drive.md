---
title: "Installation Problem with SATA drive"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by phanidee on 2009-07-18
hi,

 I have a acer laptop with SATA hard-drive.
whenever i try to boot into any of the options ("Try Ubuntu without changing the computer" or "Install Ubuntu"), i see a lot of squashfs error messages. 

When i boot with "single" in boot options, there is no hda in /dev.
so i think my sata hard drive is not being detected and thus these squashfs errors.

Please help with this problem !

Thanks in advance,
Phani.

---

### Post by presence1960 on 2009-07-18
Did you MD5SUM the iso after you downloaded it? See here: [MD5SUM]("http://help.ubuntu.com/community/HowToMD5SUM") 

Did you try "check disk for defects" when you boot the live CD?

Did you burn the CD and the slowest possible speed (4x is perfect)?

---

### Post by phanidee on 2009-07-19
Yes, md5sum did match.

burnt at slowest speed and no defects.

But still the problem exists.

after your message i thought there might be some problem with cd while burning and so created startup usb disk with this iso, and booted through that disk, still the same problem.

I saw somewhere mentioning about the sata drive and changing bios settings to "Enhanced Mode"
But my computer bios doesnt have any such option. It has two options for SATA controller mode : 1. IDE MODE 2. AHCI MODE

Iam using Acer travelmate 5720 model.

---

### Post by hvthao on 2009-07-19
You can try IDE mode!

---

