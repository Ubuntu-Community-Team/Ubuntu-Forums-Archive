---
title: "Help with Hardrive Partition"
date: 2009-07-21
forum: Hardware
---

### Post by bomboy5592 on 2009-07-21
I have a gateway laptop that has a 60 GB hardrive.  About 54 GB are used for Windows XP.  4GB are used for Ubuntu Linux.  The Windows XP Partition has 19 GB free. Last time I tried to install Ubuntu, I ran out of space on its partition and it crashed. How can I take soem of that free space from the windows partition and "give" it to the 4 GB Ubuntu Linux Partition? Is that even possible? I just need Ubuntu Linux to have more space on my hardrive, without getting rid of Windows XP.

All help is greatly appriciated.
-bomboy5592-

---

### Post by az on 2009-07-21
> **bomboy5592 said:**
> I have a gateway laptop that has a 60 GB hardrive.  About 54 GB are used for Windows XP.  4GB are used for Ubuntu Linux.  The Windows XP Partition has 19 GB free. Last time I tried to install Ubuntu, I ran out of space on its partition and it crashed. How can I take soem of that free space from the windows partition and "give" it to the 4 GB Ubuntu Linux Partition? Is that even possible? I just need Ubuntu Linux to have more space on my hardrive, without getting rid of Windows XP.

All help is greatly appriciated.
-bomboy5592-

Just boot the live cd and use the partition editor to resize the windows partition.  Delete the Ubuntu partition(s) you tried to install to and leave it all as unallocated space.

Then, start the installation and it will use the unallocated space by default.  You can just pick guided partitioning and go ahead with the install.

---

### Post by bomboy5592 on 2009-07-21
well....I tried that... maybe I'm not doing it right. Its 49.04 GB, and when I click "resize/move" I can't figure how to resize it... could you elaborate?

---

### Post by az on 2009-07-21
> **bomboy5592 said:**
> well....I tried that... maybe I'm not doing it right. Its 49.04 GB, and when I click "resize/move" I can't figure how to resize it... could you elaborate?

Maybe it has not been cleanly shut down.  Maybe it needs to be defragmented.

---

