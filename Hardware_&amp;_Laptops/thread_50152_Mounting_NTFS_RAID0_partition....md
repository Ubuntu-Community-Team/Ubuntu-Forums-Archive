---
title: "Mounting NTFS RAID0 partition..."
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by derelict_frog on 2005-07-19
Gday

I have a silicon image 3112 onboard sata chip with 2x120G drives of it in a single RAID0 NTFS partition.

I can see it in device manager, its in dev/sda1/  (whateva that means) and when i type ls /dev/mapper/     i get: casper-cow, casper-snapshot & control , i think i should be getting the names of the hdds there maybe?

Any instructions or help on adding them would be great, please tell me if u want me to type anything in or give you more information!

Thanks!!!!!

---

### Post by ubuntp on 2005-07-23
Did you try to mount it?

mkdir /mnt/raid
mount -t ntfs -o ro,user,iocharset=utf8,umask=0 /dev/sda1 /mnt/raid

Your NTFS RAID should be mounted in /mnt/raid then.

---

