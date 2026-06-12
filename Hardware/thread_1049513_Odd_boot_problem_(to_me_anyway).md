---
title: "Odd boot problem (to me anyway)"
date: 2009-01-24
forum: Hardware
---

### Post by cc_humbry on 2009-01-24
Hi,
This is an odd problem and has occured since I did a full reinstall of Intrepid on my Targa Traveller 1574 laptop. I previously had XP and 8.10 dual boot.

The laptop came (when bought) with a small Linux partition that (I think) was started when a button (not power button) was pressed on the laptop (Quick Media) it is called. I never used it and when installing and re-partioning ages ago I deleted this partition.

Now when I try and turn the computer on it doesn't boot when I use the normal power button but does when I press the Quick Media button. This is ok generally but when rebooting, or restarting following updates etc. it fails to boot again. The laptop only will boot from the Quick Media button. It won't even boot from DVD drive if set to boot first in BIOS (again, will do from the quick media button).

Is this something Grub can sort out? 
I have attached copy of fdisk (if that helps)??


Thanks for any insight into getting this resolved.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2104483+  82  Linux swap / Solaris
/dev/sda2   *         263        2873    20972857+  83  Linux
/dev/sda3            2874       12161    74605860   83  Linux


Conrad

---

### Post by cc_humbry on 2009-01-25
Anyone help with this, I know it is an odd one, but I don't know where to start looking. Not experienced with Grub, but don't even know this is where I need to start looking.
Thanks Conrad

---

### Post by 73ckn797 on 2009-01-25
> **cc_humbry said:**
> Anyone help with this, I know it is an odd one, but I don't know where to start looking. Not experienced with Grub, but don't even know this is where I need to start looking.
Thanks Conrad


Is there anything in the BIOS that you can change in relation to the media button?

---

### Post by cc_humbry on 2009-01-25
can't see anything. Only gives two options for the boot priority - hard disk or cd/dvd. Odd thing is if I have it set that cd is first boot option then even that isn't picked up by pressing the power button, only works if using the media button.
Conrad

---

