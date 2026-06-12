---
title: "[SOLVED] chroot doesn't work"
date: 2008-11-03
forum: General Help
---

### Post by Sanix on 2008-11-03
I screwed up my grub, because I "fixed" my partition table order with fdisk.

So I booted a livecd, did everything as stated in a tutorial to fix grub. But there's a problem, when I try to chroot the /mnt partition, which contains the boot directory.

> 
root@ubuntu:/mnt/bin# chroot /mnt/
chroot: cannot run command `/bin/bash': Exec format error

root@ubuntu:/mnt/bin# sudo chroot /mnt /bin/sh
chroot: cannot run command `/bin/sh': Exec format error
root@ubuntu:/mnt/bin# sudo chroot /mnt /bin/bash
chroot: cannot run command `/bin/bash': Exec format error


---

### Post by LateNiteTV on 2008-11-03
have you tried it while outside of /mnt?

---

### Post by Sanix on 2008-11-04
Yes, I tried both, same error.

---

### Post by Sanix on 2008-11-04
Do I need to reinstall everything? Because it should be running again until tomorrow...

---

### Post by Sanix on 2008-11-04
The problem was the mix between 64 and 32 bit.

---

