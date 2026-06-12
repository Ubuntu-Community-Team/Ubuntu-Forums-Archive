---
title: "Error: No Such Partition grub rescue&gt;"
date: 2010-12-05
forum: Hardware
---

### Post by [E]vent[H]orizon on 2010-12-05
Ok, so I have done something abviously stupid. I found a tutorial online on how to remove/edit partitions. There were 4 on my internal hard drive, and I was running a Linux LiveCD to do this. In the LiveCD, I used fdisk to remove all of the partitions on the hard drive. I was not dual-booting, so the only thing on my laptop was Ubuntu 10.10. After I removed the partitions, I restarted my computer and go the error message:
 
error: no such partition
grub rescue>
 
I can not boot from my USB Stick LiveCD any more, nor from the internal HD Ubuntu 10.10 installation. I need help to get this back up and running again. Any help at all will be extremely appreciated. Please, somone help me here!

---

### Post by ajgreeny on 2010-12-05
It is no surprise that you can not boot from the internal hard drive, you did delete all four partitions on it, so there is nothing there to boot.

For the USB or live CD, set the boot order to whichever you want to boot to, and that should work.  If not come back again.

---

### Post by [E]vent[H]orizon on 2010-12-06
I fixed it :) The problem with my LiveCD is that apparently the grub had been removed from it or something... so I simply reinstalled another liveCD image onto the flash drive and that worked :)

---

