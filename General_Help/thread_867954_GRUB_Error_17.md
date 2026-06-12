---
title: "GRUB Error 17"
date: 2008-07-23
forum: General Help
---

### Post by chrislynch8 on 2008-07-23
Hi,

My Ubuntu partition was deleted from my dual boot pc and now I can't get into XP either. I am booted into the Ubuntu live cd here and I can see my XP partition with all my files etc and my Ubuntu partition that is empty.

I was using grub for selecting my dual boot options and now I get the error 17 when I start the Laptop.

Any one have any ideas on how to solve this. I'm trying to install Ubuntu again in the how that it will also pick up XP, as XP is the most used and Ubuntu I used for testing programs etc.... I really need to get XP back.

Any advice is welcome and I will let ye know the outcome of installing Ubuntu again.

Rgds
Chris

---

### Post by northern lights on 2008-07-23
You can fix a messed up GRUB using the [SuperGrubDisk]("http://www.supergrubdisk.org/")

---

### Post by phidia on 2008-07-23
If you are just wanting to boot xp for now do this:

Using Windows 2000, XP, 2003 CD:

Enter into &#8220;Recovery Console&#8221; by pressing &#8220;R&#8220;, select your Windows installation and enter administrator password. Now provide following command:

    fixmbr

Press &#8220;Y&#8221; to confirm and type Exit to exit from recovery console.

---

