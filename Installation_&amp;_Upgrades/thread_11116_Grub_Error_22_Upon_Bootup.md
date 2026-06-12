---
title: "Grub Error 22 Upon Bootup"
date: 2005-01-13
forum: Installation &amp; Upgrades
---

### Post by Mic on 2005-01-13
Just installed Ubuntu and upon reboot, the screen shows something like 

Grub 1.5
Error 22.

I cannot even boot up windows now.

Believe that the copy of Ubtuntu that I downloaded may not be good.


I wanted to boot back into windows (seen somewhere about re-setting MBR, but cannot find when i need it :-( ) but do not know how.  please help.





Will try to get of a good copy of Ubtuntu and reinstalled later  :-)

---

### Post by wallijonn on 2005-01-14
Most GRUB errors denote that it cannot find a partition, cannot read a partition table, etc.

It could be as simple as setting the BIOS to read from the HD first or  changing the disc geometry to LBA, for example. The MBR could be protected by a Windows anti-virus program or in the BIOS.

If you have WXP installed, boot from the WXP CD , go to recovery mode and 'fixmbr', reboot, remove the WXP CD, and hopefully it will recognise the HD and boot into WXP correctly.

---

### Post by Mic on 2005-01-14
pc is without antivirus program so this is out.

Tried BIOS to read from the HD first, still no good.

Boot from the W2K CD, went to recovery mode and did a fixmbr and reboot.
still not luck.


Finally, did a full reformat and partition. 


Life goes on   :) 


will try to get another copy of Ubuntu, till then   8)

---

