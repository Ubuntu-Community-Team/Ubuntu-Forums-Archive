---
title: "Seagate Ironwolf 12TB with usb adapter not recognized?"
date: 2023-04-09
forum: Hardware
---

### Post by rodm1 on 2023-04-09
I have a NIB Seagate Ironwolf 12TB drive I would like to use as a usb backup drive just for home stuff photos, and files. I purchased a usb adapter at link hopping the drive would be recognized right away it's not seen by Linux. The drive on label has a 5V and 12V number dues this drive need both 5V and 12V or dues it run on both? Trying the cable in Windows disk manager not able to access and don't feel it spinning up. I was told it could be in read mode or do I need another cable with 12V any Ideas? 



[https://www.amazon.com/dp/B084ZTSMWF](https://www.amazon.com/dp/B084ZTSMWF) 

[https://www.amazon.com/dp/B011M8YACM](https://www.amazon.com/dp/B011M8YACM)

---

### Post by TheFu on 2023-04-09
Some USB converters have a size limitation for how large a drive it will work with.  I've seen 4TB limitations, for example.
My best advice is to get a different USB converter, perhaps a "dock" or switch to eSATA, which supports the entire SATA instruction set, unlike USB storage.

If the BIOS doesn't see the drive and size correctly before booting into any OS, then the OS is unlikely to see it either.  Look for a BIOS/firmware upgrade first.

---

### Post by SeijiSensei on 2023-04-15
I just bought a 14 TB external Seagate and am currently running some tests. 

[https://www.newegg.com/seagate-expansion-14tb-black/p/N82E16822184958](https://www.newegg.com/seagate-expansion-14tb-black/p/N82E16822184958)

A new device comes with a USB 3.0 cable that has a (proprietary?) wider-than-normal jack with squiggly sides that plugs into the drive. (My 2TB external Seagate has a similar jack.)  It was formatted with a small Windows-related partition and what appeared to be empty space. I used GNU parted to make a new partition that encompassed all the remaining space. Let's assume the new partition appears as /dev/sdb2. Then I used "sudo mkfs -t ext4 /dev/sdb2" to create an ext4 filesystem in the new partition. Then I could mount it into the file system just as normal with "sudo mkdir /media/big; sudo mount /dev/sdb2 /media/big". I just transferred a 2.9 GB file to it. The average transfer speed was 133 MB/s. 

I was doing this over ssh so I couldn't use gparted.

---

