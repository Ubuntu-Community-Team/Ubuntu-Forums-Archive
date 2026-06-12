---
title: "Hard Drive Problems"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by drums907 on 2006-01-17
I am trying to install Ubutu on a 15.3 GB HDD.  When I get to the partitioning section of the insallation.  The entire drive capacity is reported as 2.1 GB.  The saftware is recognizing the correct drive model but the capacity is incorrect.  How do I get the software to use Logical Block Addressing to see the entire drive.  This has already cost me a lot of time trying to find the answer.

Thanks for any help you can give.

---

### Post by gerbman on 2006-01-17
I'm not sure about the LBA question, but have you previously used the drive? Do any partitions currently exist on the drive?

---

### Post by drums907 on 2006-01-17
The drive previously had windows 2000 then windows 98 on it.  It worked just fine.  I even reloaded windows98 on it again just to verify for myself that the drive was not the issue.  I am probably not going to use the Ubuntu since that is the only machine that I can afford to have out of commission and I can't get it to work.

---

### Post by Azion on 2006-01-17
Quite odd, I thought that info would have been gotten from the BIOS or the drive itself. Do you have a boot disk for DOS?

---

### Post by drums907 on 2006-01-17
Yes I do have a DOS boot disk.  Which version?  I have several.  How would that help?

---

### Post by drums907 on 2006-01-18
I had previously had windows running on the drive.  I erased windows and all DOS partitions.  EUREKA!!! I Found IT!  There is a clipping jumper for older OSs that was installed on some IDE drives.  Changed the jumper and set for 16 Heads and VOILA!!!!  It is now recognized at full capacity!

---

