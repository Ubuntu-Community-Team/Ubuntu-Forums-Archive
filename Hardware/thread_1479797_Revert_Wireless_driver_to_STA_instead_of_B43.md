---
title: "Revert Wireless driver to STA instead of B43"
date: 2010-05-11
forum: Hardware
---

### Post by krantionline on 2010-05-11
Hi, 
I am using a HP Mini 110 netbook with Ubuntu 9.10.
I installed the broadcom wireless drivers from the synaptic package manager (b43-fwcutter).
I got 2 restricted drivers to choose from - a B43 one, and a STA one. 

I have selected B43 driver. Now, the machine hangs on the boot process. 
I found out that this is a known problem, and now i need to switch back to the STA driver to be able to connect to wireless networks. 
But as the machine hangs on the boot screen, i cant go ahead.
Please guide me through so i can boot back to my system. 

Regards,
Kranti

---

### Post by krantionline on 2010-05-12
It worked ! 
I followed the following steps:

1. On Grub Screen, Press 'E' on the recovery mode menu
2. add 'blacklist b43' to the kernel entry
3. boot to the root shell prompt
4. There, run ```
sudo apt-get install --reinstall bcmwl-kernel-driver
```
5. Reboot

---

