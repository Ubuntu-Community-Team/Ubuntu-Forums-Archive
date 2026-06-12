---
title: "Hard Disk issues, Controller Issues, Driver Issues or User error?"
date: 2011-07-27
forum: Hardware
---

### Post by Narzugon on 2011-07-27
I hate putting a vague subject line. But I'm not really sure what is the root cause of my current problems.
New Linux user here but years of experience at various levels of the IT world. A long string of events so I'll be brief but descriptive.

I "was" working with an external usb raid 1 box that flaked out. In trouble shooting that box, I at one time or another connected each of the 3 drives (two drives in the unit and a spare thats rotated in) to my Ubuntu comp to look at the disks status and or data. If I remember correctly (it's been a long two week ordeal), 2 of the 3 drives had corrupt data. I then copied the good data to my Ubuntu comp.

I got the new replacement box in (Araid S3500-GP) and tried mirroring the good drive to each of the two drives with corrupt data. No go. From here my exact steps escape me but suffice it to say that I tried various things such as formating the drives in Ubuntu (NTFS and FAT) via internal SATA connections and SATA to USB external connections and copying the data to one drive so I could test the mirroring of the second drive. All tests yeilded the same result. The mirroring process gets stuck at the beginning. 

I ran WDDiag on the two drives. It reports error 0220 or Drive Locked. WD's description reads:

Security feature of the drive reports locked status. Some vendors use  the security feature to ensure the usage of only specific drives in  their system, or the drive may have been locked by a user using a third  party utility to enable this feature. The same utility and the original  code used to lock the drive are necessary to unlock this drive. Please  contact the system vendor for the above-mentioned information.

If I now try to format in Ubuntu I'm prompted with the "Authenticate" dialogue which I assume is normal. Then the following error:

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sda: Input/output error

 SMART status in Ubuntu Disk Utility is good. With that said, have I locked myself out some how? Could it be a controller issue with Ubuntu? Here's a bit more info:

Ubuntu 11.04
SATA to USB Coolmax (no model #)
MB: Soc 478 PCChips M925G w/no SATA VIA chipset
SATA Controller Card: IO FLEX PSA150 Silicon Image chip
WD drives: WD5000AADS and WD5000AAKS

---

### Post by Narzugon on 2011-08-02
I haven't gotten any further on this. Here's hoping someone has ran into this before and knows the answer! :confused:

---

