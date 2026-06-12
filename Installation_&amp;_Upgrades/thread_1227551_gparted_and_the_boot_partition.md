---
title: "gparted and the boot partition"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by graphicsxp on 2009-07-30
Hi,

I'm having nightmares because I can't install Windows Server 2008. I'm having the same issue as other people, which is described and (apparently) solved here [http://www.vistax64.com/vista-installation-setup/2953-windows-unable-find-system-volume-6.html#post417782](http://www.vistax64.com/vista-installation-setup/2953-windows-unable-find-system-volume-6.html#post417782)

Now this guy is saying to set the ntfs partition as the boot partition in GParted. Fine, I can do that. But I can also foresee that if things go wrong, I'll need to set the boot partition back to my Linux partition..

So, I could use the Live CD to do that, but I can never log in in graphical mode (I always get an X error). 

However I can launch a terminal. But then how do I set the boot partition with the command line ?


Thanks

---

### Post by dstew on 2009-07-31
If by "setting the boot partition" you mean setting the partition boot flag, you do not need to do this for Linux. Only Windows needs the boot flag set. The Windows boot loader uses this flag to find its system partition. In Linux, the system partition is designated when grub is installed. Grub does not look for the boot flag.

---

### Post by graphicsxp on 2009-07-31
Hi,
Thanks for helping

That's exactly the point :) I was trying to set the boot flag to the partition on which I intended to install Windows Server. Otherwise the installation failed.

I did this using Parted in command line.

All is fine now :)

---

