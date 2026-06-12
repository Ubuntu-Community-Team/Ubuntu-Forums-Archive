---
title: "Ubuntu wiped vista recovery"
date: 2008-10-12
forum: General Help
---

### Post by Monotoko on 2008-10-12
Hiya guys, i had a duel-boot system with both ubuntu and vista, it went rather wrong (my fault, i played a bit with GRUB) so i decided to wipe C:\ and start again, so i wiped it, there were two partitions on it, C:\ and the vista recov partition that came with the machine.

I had a successful install of Ubuntu, and was gonna put vista on, so i set up the partition, put the disk in, rebooted, and got a message saying "the recovery partition cannot be found"

I assume i musnt have partitioned properly and used all the space, wiping over my recov partition.

I know this is a bit of an awkward question to ask on the ubuntu forums, but i dont know any community as computer litterate as you guys, and i was wondering if you would mind telling me if i can get that partition back so that i can duel-boot again.

---

### Post by lisati on 2008-10-12
> **Monotoko said:**
> Hiya guys, i had a duel-boot system with both ubuntu and vista, it went rather wrong (my fault, i played a bit with GRUB) so i decided to wipe C:\ and start again, so i wiped it, there were two partitions on it, C:\ and the vista recov partition that came with the machine.

I had a successful install of Ubuntu, and was gonna put vista on, so i set up the partition, put the disk in, rebooted, and got a message saying "the recovery partition cannot be found"

I assume i musnt have partitioned properly and used all the space, wiping over my recov partition.

I know this is a bit of an awkward question to ask on the ubuntu forums, but i dont know any community as computer litterate as you guys, and i was wondering if you would mind telling me if i can get that partition back so that i can duel-boot again.

The first thing to do, before panicking, is log into Ubuntu, using the Live CD if necessary, go to the terminal, and enter the following command:
```
sudo fdisk -l
``` 
Posting the output will help us tell (amongst other things) if your vista partition is still there. The suggestions we come up with will depend in part on what fdisk shows us.

---

### Post by p_quarles on 2008-10-12
You can't, unfortunately. Many computers that ship with "recovery" partitions also include software that creates installation CDs from this partition. If you did not use that software already, you are out of luck. The chances of successfully recovering an overwritten installation partition are pretty low. Basically, you'll need to contact the manufacturer to request recovery media, most likely at your expense.

---

### Post by Monotoko on 2008-10-12
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29652   238179658+  83  Linux
/dev/sda2           29653       30401     6016342+   5  Extended
/dev/sda5           29653       30401     6016311   82  Linux swap / Solaris


It was on sda1.....

---

### Post by p_quarles on 2008-10-12
> **Monotoko said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29652   238179658+  83  Linux
/dev/sda2           29653       30401     6016342+   5  Extended
/dev/sda5           29653       30401     6016311   82  Linux swap / Solaris


It was on sda1.....
No, it was not. /dev/sda1 is the name of the partition that Ubuntu created for itself. The results you posted show that you wiped the entire disk -- as I said, you will need to procure replacement recovery media from the manufacturer of the computer.

---

### Post by lisati on 2008-10-12
> **Monotoko said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29652   238179658+  83  Linux
/dev/sda2           29653       30401     6016342+   5  Extended
/dev/sda5           29653       30401     6016311   82  Linux swap / Solaris


It was on sda1.....

Looks like Vista has gone: as p_quarles has said, your chances of getting it back are slim to none. Your best bet if you want Vista back (for whatever reason, this isn't a "Windows bashing" thread) is to talk nicely to the people you got your machine from and/or the manufacturer to see if you can get hold of a replacement recovery disk. 

Be very cautious about the "don't ask too many questions where it came from" kind of disk: as well as  the potential for legal hassles, there's also a strong risk of nasty things like viruses and spyware creeping on to them.

---

