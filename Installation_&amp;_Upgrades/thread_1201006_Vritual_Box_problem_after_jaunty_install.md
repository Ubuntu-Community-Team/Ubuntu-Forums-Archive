---
title: "Vritual Box problem after jaunty install"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by zaffod on 2009-06-30
Hi all,

I have an issue launching an XP virtual machine in Virtual Box after upgrading from Gutsy 7.10 to Jaunty 9.04. 

Actually, I did a clean install not an upgrade. 
I have /home on a separate partition so I was able to keep all my files intact. 

After the install and update of jaunty, I installed Virtual Box from the repos but found it was the OSE edition. So I uninstalled it and downloaded the latest version and installed that. 

Installed fine. Added myself to the vboxusers group. The app launches fine. I added my xp.vdi hard disk to Virtual Box and tried to start it. No matter what I try, it just blue screens when starting. 

Don’t know if it matters, but I installed the system as ext4 but kept /home as ext3. So the xp.vdi file is on an ext3 partition but the OS is ext4. 

Short of searching for Windows booting help, any one had a similar experience? 
Or any one know what may cause Virtual Box to behave like this after an upgrade?

Cheers.

---

### Post by zaffod on 2009-07-01
In case anyone else has this issue, I fixed it by changing the Virtual Box Hard Disk settings: IDE Controller Type to PIIX3 instead of PIIX4
and 
Enabling IO APIC which had become unchecked. 

All good now.

---

