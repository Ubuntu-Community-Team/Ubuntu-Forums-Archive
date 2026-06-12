---
title: "Dual Boot guide for IBM Thinkpad T42?( Kubuntu 7.04)"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by zhuanyi on 2007-06-19
Hi,
i am just wondering whether there is any dual boot guide for Kubuntu 7.04 and WinXP running in an IBM T42, and does not break my MBR? :D
Thanks a lot!

---

### Post by Median on 2007-06-19
I'm not sure about a guide but I was able to use this website [http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/") a lot during my install.  I installed Ubuntu 7.04 on my T42 with minimal issues (don't try and use the Service partition as Swap, that messed me up really bad lol).  Using the built in partitioning app in the Ubuntu installer was fairly simple, and after I fixed my issue regarding the misused Service partition the install was really clean.

---

### Post by ivanhelguera on 2007-07-04
i did not try it, but just found this
[http://gawrysiak.org/corvus/?p=4]("http://gawrysiak.org/corvus/?p=4")
hope it helps, 
ih

---

### Post by Helvidius on 2008-02-22
Please let me know how that goes.  I just bought a T42 on eBay for a good price and am thinking about replacing WinXP with Ubuntu.

*Mark*
> **zhuanyi said:**
> Hi,
i am just wondering whether there is any dual boot guide for Kubuntu 7.04 and WinXP running in an IBM T42, and does not break my MBR? :D
Thanks a lot!

---

### Post by astrauch1968 on 2008-03-12
I just installed ubuntu 7.10 on a t42p (almost 4 years old). If you get one in ebay that isn´t screwed up, boot xp and make rescue disks from your data and the system with the blue "access ibm" button.
Then defragement the harddrive (using xp) and use gparted live cd to shrink your xp partition. Now reboot xp (!).
I then installed ubuntu in the free diskspace.
Yes, that way ubuntu rewrites the mbr. But somehow grub (the boot loader) is smart enough to give you the rescue partition as a boot option. :) It works, I tried it out to the point that the rescue started booting up its own os.
This should be fine for most bad things. And when you want to restore to factory state you can easily do so with the boot options.

P.S. be careful though not to mount the rescue partition. It should stay untuoched. I did not manage to keep it hidden with the bios options for the rescue partition.
P.P.S maybe the gparted stuff is not necessary and can be done with the ubuntu installer.

---

