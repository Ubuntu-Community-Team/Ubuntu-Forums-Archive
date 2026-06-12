---
title: "vista won't install on logical right? how can i copy my set up?"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by maxlstylee on 2009-08-28
Howdy..

/dev/sda1   ext3  /    7.45GiB   boot
/dev/sda2   ext        67.07GiB
    /dev/sda5   linux-swap 478.47MiB
    /dev/sda6   ntfs   66.61GiB

It appears that I can't install Vista on the nfts partition since the sda1 is the Primary partition.

I have an external Hard Drive 80GB hard drive that is recognized by Jaunty. Could I copy my linux (appx 3.10 of 7.45 used) setup onto the external hard drive and then wipe the hard drive so I could make Vista the primary drive?

I don't want to just reinstall because I've spent time working to get my Wlan 1390 wireless card working.

Thanks

---

### Post by maxlstylee on 2009-08-28
meh. nm.
didn't take that long to get the card working. will just wipe and reinstall. thanks.

---

### Post by presence1960 on 2009-08-28
why not delete the NTFS in the extended partition and then shrink the extended partition. use the unallocated space to create a primary NTFS partition for windows.

---

