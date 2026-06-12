---
title: "Installing to a LVM2 stripe"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by RJARRRPCGP on 2009-07-01
I was following this HowTo:

[https://help.ubuntu.com/community/StripedVolumeHowTo](https://help.ubuntu.com/community/StripedVolumeHowTo)

And after finding out there appears to be a typo for 

this one: ```
sudo mkfs.ext3 -m 0 /dev/!MyVirtualGroup/lvol0 
```

I didn't get an error when I took out the exclamation point so it looks like this:

```
sudo mkfs.ext3 -m 0 /dev/MyVirtualGroup/lvol0 
```

But it seems like I screwed up, it seems to just be using the first HDD. :( 

Still reports roughly 50 GB.

I have 2 PATA HDDs, one Maxtor 6Y060P0 (60 GB) and one Seagate Barracuda 7200.10 ST380215A (80 GB) and made both partitions intended for LVM2 at 56.3 GB or about that. 

Thus, should I see like 110 GB?

---

### Post by RJARRRPCGP on 2009-07-03
I found the solution, ignore this HowTo and just install with the "alternate" CD. 

It appears that you can easily configure RAID 0 from the alternate installer. ;)

Checked the file systems with System Monitor after and it looks fine, I have "md0" for the root partition at 105.8 GB, which means it's using both HDDs! 

And I created a separate partition for /boot and set the bootable flag for the /boot partition.

Maxtor 6Y060P0, primary, this one has GRUB and the /boot partition. 

-and-

Seagate Barracuda 7200.10 ST380215A

---

