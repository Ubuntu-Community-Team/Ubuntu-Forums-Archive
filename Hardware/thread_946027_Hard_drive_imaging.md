---
title: "Hard drive imaging?"
date: 2008-10-12
forum: Hardware
---

### Post by chimerical_brio on 2008-10-12
I need to install Windows on my laptop because of specific software, but I won't be using it regularly. Thus, I want to install Windows onto an external HDD, which isn't directly possible, but my plan is to create a partition for Windows, install it, copy the partition to the HDD, delete the partition, and boot from USB drive when necessary. Does that sound plausible? Does anyone know of any resources/how-tos/programs to accomplish this? I'm assuming I need to make an image of the partition and then somehow transfer it to the drive. Beyond my theoretical plan I know nohting. Thanks.

---

### Post by cariboo on 2008-10-13
Your plan may not work as NTLDR needs to be on the first partition of the first hard drive. If you don't plan to use windows often, why not use VMWare or Virtualbox to install windows on a vm, that way you've got it when you need it.

Jim

---

### Post by chimerical_brio on 2008-10-13
Hmm...the reason I can't do that is I need access to hardware, which isn't supported under VirtualBox. Are you telling me it's definitively not possible to install XP on an external HD? I mean, I think I can spare 3 GB for Windows, I'd just...rather not. But better to know I have no other choice than to waste time trying. Thanks.

---

### Post by Zimmer on 2008-10-13
[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)
many other links out there, there is also the pendrivelinux site that has a lot of info re putting OS's onto external drives (mainly \USB pendrives)

---

### Post by az on 2008-10-13
> **cariboo907 said:**
> Your plan may not work as NTLDR needs to be on the first partition of the first hard drive. If you don't plan to use windows often, why not use VMWare or Virtualbox to install windows on a vm, that way you've got it when you need it.

Jim

I know you can install Vista on any partition you have, so long as it is marked as bootable and is big enough.

You can boot Vista using grub, so you can keep it on a USB drive and use grub to boot into it.

---

