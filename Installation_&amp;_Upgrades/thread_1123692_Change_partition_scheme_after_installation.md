---
title: "Change partition scheme after installation"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by vinceshaw on 2009-04-12
I have a triple-boot on a Macbook: Leopard, Vista, Ubuntu810. 
The original partition scheme is:
1. EFI; 2. Leopard; 3. Vista; 4. Linux-boot; 5. /root; 6. /home; 7. /swap.
It worked fine but one inconvenience: within first-four mbr lines, there is no partition for data with which three OSes can communicate. 

To overcome this drawback, I decided to move Leopard beyond four as it can boot either from first-four mbr lines or GPT line beyond four. The new partition scheme is:
1. EFI; 2. Vista; 3. Fat-32 data; 4. /boot; 5. Leopard; 6. /root; 7. /home; 8. /swap.

I backed-up OSes, re-arrange the partitions and restore the OSes and data back.
Mac-Leopard worked immediately; Vista worked after a two-minute boot repair and a reboot; but Linux is a headache. I backup and restore it with Partimage from SystemRescueCD, it worked fine. And after restore, I mounted the three partitions within SysResCueCD and checked the data integrity. I manually edited /root/etc/fstab to reflect the change. After reboot, the rEFIt boot menu show Linux item but it did not boot: it was just silent, no complaint for several minutes, them jump to windows to boot. 

I wonder, does Ubuntu allow this change? Did I miss something else?

Any suggestion is highly appreciated.

Vince.

---

