---
title: "how to remove new kernel-image (falling back on old one)?"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by Harriak on 2009-08-28
Hi,,

The last linux generic update (2.6.24-24.26) on my Hardy Heron version didn't install well on my computer. Amazingly the machine said that there wasnot enough space to do so (2,5 Gb of space seems enough to me. Now upped it to 10 Gb...)
Since then the installation of all of the updates via Update Manager contain errors (f.e "linux-image-2.6.24-24-generic: subprocess post-installation script returned error exit status 2").
Checked all kinds of forum inputs relating to this problem and tried several options via Terminal. But was not succesfull.

I now consider removing the whole of linux kernel version 2.6.24-24.
Can this be done or is this too risky?
(I would 1st reboot in the former linux generic version (2.6.24-23) and 2nd mark for complete deletion all of the linux elements containing "2.6.24-24"
Is there a not so complicated way out via Terminal?

cheers harriak

---

### Post by running_rabbit07 on 2009-08-28
go to synaptic package manager and install startupmanager. Once installed, fire it up and click the scroller and pick which kernel you want to boot.

Take note that my screenshot does not include the older kernel that you want, but your startupmanager will. I just installed with the newest ISO which had the newer kernel.

---

### Post by stlsaint on 2009-08-28
be very careful when doing this as i did and had to re-install entire system...i couldnt get into vbox or install anything...not trying to scare you but be sure and do lots of research prior to doing anything!!

---

### Post by Harriak on 2009-09-01
Thanks for your suggestion Ronnie! It all worked well:

1. Backupped all files. 
2  Set startup manager to last but one kernel version. 
3. Rebooted into this particular kernel version. 
4. Marked all of the elements of the newest kernel version for complete removal in the Synaptic Pakage Manager. However: this didn't apply to the "linux-restricted-modules-comn [kernel version] (non free helper script), because it's removal would have meant to also remove part of the for last kernel version, the one I wanted to keep...), and appliance.
5. Rebooted
6. Implemented the download and complete installment of some new programmes presented through the Update Manager (this time without the forementioned error).

cheers, Harriak

---

