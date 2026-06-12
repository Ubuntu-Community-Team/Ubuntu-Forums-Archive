---
title: "Hardware raid controller not detected by installer"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by eventures on 2005-07-01
I have a Silicon Image SiI3114 raid controller with two 80gb drives set to raid 0

the ubuntu installer does not recognize this and sees the drives as two seperate drives.

Is there a solution to this? I'm not too excited about setting up software due to performance concerns.

If there isn't a solution to this, which linux distro would you recommend? 

This is for a web server machine.

---

### Post by alastair on 2005-07-02
You probably cannot use the controller in RAID mode for an install.

But I would definitely not worry about performance with Linux s/w RAID - 0 or 1 (1 is better for data protection ofcourse). I run MD RAID-1 on 2 production servers (SATA drives) and performance is good.

Forget SiL RAID, use Linux MD RAID.

---

