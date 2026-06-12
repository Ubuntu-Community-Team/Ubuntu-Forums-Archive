---
title: "Harddrive Help!"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by breaking on 2008-01-17
Hi, when i first tried to use fdisk, it was working fine i was able to write the partions, when i typed mkfs -t ext2 /dev/hda5 it said it was in use, so i deleted partions and so on, with no luck. I started playing around with fdisk and now it shows i only have 130 clyinders. Anyway to put that back to the 9000 or so that i should have? i did a full format with windows with no problems. Any Ideas/Suggestions? Thank you for all your help

Edit: I tried changing the amount of cylinders and it wouldnt keep the setting... ever time i tried to write it said, unable to write

---

### Post by Yellow Pasque on 2008-01-17
Does the BIOS recognize that many cylinders? If not, it might be time for a new hard disk :/

---

### Post by breaking on 2008-01-17
My BIOS dosnt show many cylinder it has, but i found that info when it was plugged in, under drive info... I can make partions on it (using the full drive) in windows with no errors, so im thinking the cylinder setting is messed up...

---

### Post by Yellow Pasque on 2008-01-17
I'm very confused, please post output from:
```
fdisk -l
```
(that's a lower-case L after the hyphen)

---

### Post by breaking on 2008-01-17
There are no partions, but on the desktop i see how many ever partions i set up threw partion magic...  everything that it displays is correct except the amount of clyinders...

EDIT: Results of** fdisk -l /dev/hda**

Note: sector size is 2048 (not 512)

Disk /dev/hda: 4324 MB, 4324229120 bytes
255 heads, 63 sectors/track, **131 **cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

Disk /dev/hda doesn't contain a valid partition table

---

### Post by Yellow Pasque on 2008-01-18
Partition Magic? I'm guessing that's the reason fdisk doesn't read the geometry or partition table.

I don't know of any cylinder setting that you can write to, other than manually defining drive geometry in the BIOS. After that, programs should be **reading** drive geometry info.

---

### Post by breaking on 2008-01-18
how would i do that? i dont think i have that option in my bios. If i were to format it with a windows disk, do you think that would help?

---

