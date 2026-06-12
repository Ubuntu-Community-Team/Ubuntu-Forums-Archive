---
title: "Quick ext4 question"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by Ssurno on 2009-08-04
I want to dual boot Vista and Kubuntu.  I have space allocated for Kubuntu, but I want to install it using ext4 instead of ext3.  Does Kubuntu's GRUB support ext4?  I know sidux patched theirs that way it boots ext4...Does Kubuntu boot ext4 without making a seperate ext3 boot partition?  If so I will do this:

Vista (140GB)
Swap (6,000mb)
/ ext4 (rest of HDD)

---

### Post by 1/0 on 2009-08-04
Generally no. I'm not 100 if its patched but I'd say you would have to install the dev version of GRUB2 in order to do that. But that is only my guess.

---

### Post by Sef on 2009-08-04
I would think it would.   The backend on Ubuntu and Kubuntu are the same.

Also your swap really shouldn't be more than 1 gb or 2 gb at the max.   If you need more swap, then get more ram.

---

### Post by presence1960 on 2009-08-04
> **Ssurno said:**
> I want to dual boot Vista and Kubuntu.  I have space allocated for Kubuntu, but I want to install it using ext4 instead of ext3.  Does Kubuntu's GRUB support ext4?  I know sidux patched theirs that way it boots ext4...Does Kubuntu boot ext4 without making a seperate ext3 boot partition?  If so I will do this:

Vista (140GB)
Swap (6,000mb)
/ ext4 (rest of HDD)

Of course Kubuntu's GRUB supports ext 4. Ext 4 is given as an option when partitioning. Why would the installer give you an option which can not boot. I have Jaunty's GRUB on MBR of my first boot drive. I run Jaunty & Sabayon 4.1 (ext4) and Mint5 (ext3). Jaunty's GRUB handles that just fine along with Win 7 RC!

> Also your swap really shouldn't be more than 1 gb or 2 gb at the max. If you need more swap, then get more ram.
The only reason to have more swap is if you have more RAM and want to use suspend/hibernate. Then it is recommended to have the same amount of swap as RAM. other than that Sef is correct

---

