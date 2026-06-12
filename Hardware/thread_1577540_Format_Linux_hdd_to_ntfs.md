---
title: "Format Linux hdd to ntfs"
date: 2010-09-19
forum: Hardware
---

### Post by KefkaFF on 2010-09-19
When I try to install Windows on one of my Linux HDD's with the boot CD it says that I can't install it because the drive is not NTFS. How would I format one of my Linux HDD's to NTFS so that I am able to install Windows on it?

---

### Post by IcarusR on 2010-09-19
What do you mean by..

> Linux HDD

Hard drives are neither linux nor windows. They can be formatted for either & have either installed on them.

Do you have any OS installed on this HDD ??

A genuine Windows CD should be capable of formatting to ntfs as part of the install routine.

---

### Post by ugm6hr on 2010-09-19
Use your Ubuntu LiveCD to format it with GParted (Partition Manager). You can format as "FAT" or "NTFS"

The Windows installer will also offer to reformat for you.

---

### Post by srs5694 on 2010-09-19
Do you want to *completely replace* Linux or *add Windows* to a disk that's already used by Linux? The optimum solutions vary depending on which of these things you want to do. If the latter, post a screen shot of your current partition setup (taken from GParted or a similar tool), or post the output of typing "sudo fdisk -lu" at a shell prompt, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

