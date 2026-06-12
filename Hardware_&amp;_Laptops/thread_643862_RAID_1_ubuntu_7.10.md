---
title: "RAID 1 ubuntu 7.10"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by erwin_viafrica on 2007-12-18
Hi all,

I'v just installed Edubuntu 7.10 on my machine and in RAID 1-configuration. 
I've installed grub into the second disk. When unplugging the first hd, the second starts with the boot loader, but doesn't go further, so seems not to be able to find the disk. 

What I have: 
/dev/sda
/dev/sdb

/dev/md0 (/)
/dev/md1 (swap)

What I did after the installation: 
sudo grub-install /dev/sdb
sudo grub
device (hd0) /dev/sdb
root (hd0,0)
setup (hd0)
root (hd0,0)
setup (hd0)
quit

I even entered fallback-items into grub's menu.lst, but none worked. 

Any ideas?

---

