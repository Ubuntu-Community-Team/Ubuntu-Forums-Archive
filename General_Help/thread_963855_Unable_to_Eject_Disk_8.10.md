---
title: "Unable to Eject Disk 8.10"
date: 2008-10-30
forum: General Help
---

### Post by czechman86 on 2008-10-30
Hello All and Happy 8.10 Day!

I am having problems ejecting my disk on 8.10. Whenever I try to eject the cd drive, it opens half way and then shuts. Even running 'eject' and 'sudo eject' from the terminal do little to no good. Is there a work around with the /etc/fstab file or another possible work around? Any help or suggestions would be great! Thank you!

Edit: The drive ejects fine with Arch Linux and 8.04, so I doubt it is due to faulty hardware.

Edit 2: After the update, I am now able to eject the disk from the terminal by using either 'eject' or 'sudo eject'. Still no dice with the standard ejection procedure.

---

### Post by raldz on 2008-10-31
you are not alone.. i'm also having the same problem with Ibex.. searching the forum for solutions..

---

### Post by fart_flower on 2008-10-31
Me too.  Same problem.

---

### Post by raldz on 2008-10-31
bug report and suggested fix here:
[https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931)


suggested fix is to edit:
/etc/udev/rules.d/60-persistent-storage.rules

and add/change this:

> # skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"
ENV{DEVTYPE}=="disk", KERNEL=="sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

---

### Post by czechman86 on 2008-11-01
Awesome! Ill give it a try and let you know how it goes!

---

### Post by rfurman24 on 2008-11-13
Applied the patch and still broken.

---

