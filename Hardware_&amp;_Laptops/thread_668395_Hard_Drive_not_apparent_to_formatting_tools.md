---
title: "Hard Drive not apparent to formatting tools"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by pbottjen on 2008-01-15
I installed Ubuntu 7.10 on my work laptop (Thinkpad T61)
Now I need to put Windows back on.
When I start the windows setup, it tells me that I dont have any hard drives installed.
None of my 3rd party disk formatting tools can see the hard drive either.
Ubuntu runs just fine.
I started the live disk, used gparted to delete all the partitions and create one NTFS partition hoping the Windows setup would see it then.  No luck.
Any suggestions?

---

### Post by logos34 on 2008-01-15
Use gparted to delete the ntfs and start with an empty disk.

If windows still doesn't see it, try [wiping it with this.]("http://dban.sourceforge.net/")

---

### Post by pbottjen on 2008-01-15
Thanks for the suggestion,  DBAN was one of the 3rd party wipers that I tried.
I think I found the problem however, it has something to do with AHCI settings in the BIOS.
Apparently the WinXP disk that I am using does not support AHCI.  I switched to "Compatibility Mode" and am installing now.
Linux was not the problem, it was Windows.

---

### Post by logos34 on 2008-01-15
> **pbottjen said:**
> Thanks for the suggestion,  DBAN was one of the 3rd party wipers that I tried.
I think I found the problem however, it has something to do with AHCI settings in the BIOS.
Apparently the WinXP disk that I am using does not support AHCI.  I switched to "Compatibility Mode" and am installing now.
Linux was not the problem, it was Windows.

hmm...interesting.  Well, glad you fixed it.  Good luck.

---

### Post by Omnios on 2008-01-15
Hi if you ahd grub installed you might have to fix the MBR boot with the Windows disk.

 There are many posts here on how to do this.

---

