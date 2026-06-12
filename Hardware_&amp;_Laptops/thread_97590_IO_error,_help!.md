---
title: "I/O error, help!"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by Wizzard on 2005-12-01
Hi. 
A few days ago, I recieve following messages during boot:
Buffer I/O error on device dm-0, logical block....

What does it mean? Do I have some bad sectors on the disk? Both of my disks are new, 160 and 120 GB Maxtor drives... What can I do?

---

### Post by ape on 2005-12-01
Can you please post the error message in its entirety?  I don't recognize dm-0 as a valid device name.  

You can also run the dmesg command and search for this error to see if there is any more information.

---

### Post by Wizzard on 2005-12-02
OK, I found out it is an hardware error. I wonder that Linux found that error on NTFS partition with WinXP installed and Windows found nothing... Then I launched scandisk and it was confirmed... I have to replace the disk.

---

