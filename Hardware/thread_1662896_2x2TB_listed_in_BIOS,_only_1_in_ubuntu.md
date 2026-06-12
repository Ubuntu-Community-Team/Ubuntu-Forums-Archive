---
title: "2x2TB listed in BIOS, only 1 in ubuntu"
date: 2011-01-08
forum: Hardware
---

### Post by hansoffate on 2011-01-08
I just bought 2 identical drives to setup as RAID 1 or as a zfs mirror (still haven't decided).  Anyways, I booted my system after installing both drives and both were listed in the BIOS.  Great, I was well on my way.  I booted into my 10.04 LTE install and checked disk utility.  There are two SATA controllers listed: the first with a 1tb and a 2tb, and the second with a 37gb only.  On the second controller, there should be another 2tb drive listed.  Any ideas on what to do?  Let me know if you need any more information.

Thanks
-Hans

OS: 10.04
Drives in question: 2xSamsung HD204UI 2TB

Solved.  I just had to update the linuximage

---

### Post by jmate24 on 2011-10-28
Zfs does not work with Ubuntu if you are using raid 1 then you are mirroring and not striping (raid 0) the best option if you have several drives with different sizes in your computer is to set up and LVM 'Logical Volume Management' that will consolidate all of your hard drives into one but there is no fault tolerance like with a RAID 5 (striping with parity) but you will be able to maximize your space with it and you can add or subtract hard drives when ever you need to just remember that if you have data on one of those drives you cannot subtract it easily that is why it is best to have a backup of all of your files (or if you feel enthusiastic and have a little extra cash lying around then you could build an NFS (Network File Server) Computer that you can have all of your files on it and safe from destruction if one of those drives bellies up.) Otherwise my option would be to keep both 2TB hard drives and Partition the first drive like this:

Create a /boot partition 384MB 
> Create an Extended Partition for the rest of the 2TB then a / partition of 383GB 
> swap partition 2x as much as your amount of RAM lets say 17GB 
> /var partition 400GB 
> /usr partition 400GB 
> /opt partition 400GB 
> /tmp partition 400GB 
then use the second 2TB Drive as your /home partition.

---

