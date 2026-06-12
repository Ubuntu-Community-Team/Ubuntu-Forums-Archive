---
title: "Pre-Install Partition Question"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by ferebee on 2006-01-09
Hello there!

I'm relatively new to Linux ( Dual booting Mepis and Winxp for a few months now and really enjoying it. :)  Only boot back into Windows for itunes and my nephew's
favorite kids games)  I'm interested in trying out Ubuntu on Hdd as well.

I'm wondering if I can use Qtparted  from Mepis to pre-partition my free hard drive
space for the Ubuntu install? Will this cause any problems for the installer? I use Mepis with separate /root and /home partitions and am thinking of the same setup for Ubuntu. 

Also, would I need to create another swap partition, or will Ubuntu use the one I created for Mepis? (Mepis and Ubuntu will be on separate hard drives.)

---

### Post by az on 2006-01-09
[QUOTE=ferebee]Hello there!

I'm relatively new to Linux ( Dual booting Mepis and Winxp for a few months now and really enjoying it. :)  Only boot back into Windows for itunes and my nephew's
favorite kids games)  I'm interested in trying out Ubuntu on Hdd as well.

I'm wondering if I can use Qtparted  from Mepis to pre-partition my free hard drive
space for the Ubuntu install? Will this cause any problems for the installer? I use Mepis with separate /root and /home partitions and am thinking of the same setup for Ubuntu. 

Also, would I need to create another swap partition, or will Ubuntu use the one I created for Mepis? (Mepis and Ubuntu will be on separate hard drives.)[/QUOTE]

Sure you can use another partitioner (all linux partitioners use GnuParted which works very well.) but the installer will default to detecting a big partition and offering to shrink it for you.

As for theswap, you can use one swap for both OSes since you will not be using them at the same time.  However, suspend-to-disk (hibernation) writes your ram to the swap before shutting down.  If you use your swap for another OS, your data will be gone.

I hibernate my desktop all the time.

---

### Post by ferebee on 2006-01-09
[QUOTE=azz]Sure you can use another partitioner (all linux partitioners use GnuParted which works very well.) but the installer will default to detecting a big partition and offering to shrink it for you.

As for theswap, you can use one swap for both OSes since you will not be using them at the same time.  However, suspend-to-disk (hibernation) writes your ram to the swap before shutting down.  If you use your swap for another OS, your data will be gone.

I hibernate my desktop all the time.[/QUOTE]




I don't hibernate my computer, but since I'm not the only one who uses this computer and accidents do happen I guess I'd better give Ubuntu it's own swap, just to be on the safe side.

Thanks for your help!

---

