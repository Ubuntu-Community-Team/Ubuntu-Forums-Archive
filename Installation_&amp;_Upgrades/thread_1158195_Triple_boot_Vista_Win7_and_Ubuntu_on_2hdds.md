---
title: "Triple boot Vista Win7 and Ubuntu on 2hdds"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by noneedfor_id on 2009-05-13
Hi and am somewhat new to Linux. I would like to install win7 and ubuntu on a single hard drive while having vista on a primary drive is this at all possible?

---

### Post by 73ckn797 on 2009-05-13
Install Win 7 then Ubuntu. The LiveCD will create the doot menu on it's own as part of the installation process. Windows likes being first.

First partition the second drive with the LiveCD making the first one NTFS and second ext3 for Ubuntu.

---

### Post by noneedfor_id on 2009-05-13
Thanks for your response. Ok so then which bootloader will handle all OS? Vista's or will GRUB do the work?

---

### Post by Aaric on 2009-05-13
Grub will do the work for the HD that Ubuntu is installed on(during the install the Windows installations will be added to grub). For the second HD you have to set your bios to boot from external HDs. I am quad booting Vista, XP, Windows 7, and Ubuntu on one HD.

---

### Post by noneedfor_id on 2009-05-13
Well last night I installed Win7, on 2nd HDD and by default I would get a boot menu for either Win7 or Vista... So now Ill have to manually boot from one HDD or the other?

---

### Post by 73ckn797 on 2009-05-13
> **noneedfor_id said:**
> Well last night I installed Win7, on 2nd HDD and by default I would get a boot menu for either Win7 or Vista... So now Ill have to manually boot from one HDD or the other?


The Ubuntu installation will set up the boot menu with all operating systems listed. It may default to Ubuntu as the primary system if nothing else is selected when the boot menu comes up initially but that can be changed later, if you desire. The Windows generated boot menu will not come up.

---

### Post by noneedfor_id on 2009-05-13
Thanks for the input. Im backing up files now, Ill post after I finish installations. :guitar:

---

### Post by noneedfor_id on 2009-05-13
Hooray!! It worked!. I made a little mistake though, I mounted the boot loader to "sdb" instead of "hd0" buts its tolerable, I would just have to choose which disk drive to boot from, no worries. 
Thanks for all your help guys.):P

---

