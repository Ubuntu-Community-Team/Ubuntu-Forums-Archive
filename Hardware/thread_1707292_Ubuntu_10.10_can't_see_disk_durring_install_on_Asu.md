---
title: "Ubuntu 10.10 can't see disk durring install on Asus A8N-SLI Premium nForce 4 SLI"
date: 2011-03-15
forum: Hardware
---

### Post by Denbert on 2011-03-15
Hi,

I'm trying to setup a clean Ubuntu 10.10 32-bit on Motherboard: Asus A8N-SLI Premium nForce 4 SLI

But the Ubuntu installer can't see the HDD?

Ive tried the NForce SATA and Silicon SATA ports whitout any success :-(

Anyone with a suggestion?

---

### Post by Rubi1200 on 2011-03-15
Hi,
from the LiveCD, post the output of these commands:

```
sudo fdisk -lu

sudo parted -l
```

---

### Post by Denbert on 2011-03-16
Hi, well I tried the suggested LiveCD option and hit Try Ubuntu instead of the normal Install.

After the LiveCD system was up i tried to choss install from the desktop, and bingo the installer could see all disks, and I where able to install the system. IMO it's a bug! - But I'm happy now, thanks for the suggestion about try the LiveCD solution.

---

### Post by Rubi1200 on 2011-03-16
Glad you got it sorted out in the end.

Enjoy :-)

---

