---
title: "RAID0 on installed system"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by prvul on 2007-05-21
I have some old (PIII 500MHz, 256 MB RAM) PC. I have installed feisty on 9GB HD (/dev/sdb, swap 444MB, / rest). I have same second disk (/dev/sda) which is empty. Could i setup RAID0 with them without reinstalling the system?

---

### Post by kragen on 2007-05-21
No you can't: You can only create a RAID 0 array from formatted partitions.

Just in case you were thinking of doing something clever :P - You could make a backup of your Ubuntu installation, create the raid 0 arrays and copy your existing installation back... but it wouldn't work. You're existing Ubuntu installation doesn't have the packages needed to mount and access the raid drives installed, and all the partitions would changing meaning you would need to update fstab.

In fact, I suppose it might work, but I wouldn't recommend it.

Short answer: No :P

---

### Post by Gagle on 2007-05-21
It will be much simpler to re-install the whole thing.  One of my fellow scholar attemtepd a similar experience, using kragen 's approach with manually edited installation scripts for the drivers and a proper mounting of the drives, but failed miserably after a couple reboot.  The system wasn't stable and he lost a lot of data.
It did work though,for a second or two... so maybe if professionnal programmers get to it you could see your problem resolved in the future.

---

