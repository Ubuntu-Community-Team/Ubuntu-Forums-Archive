---
title: "Jaunty RAID0/Encryption/LVM sluggish performance"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by begoogled on 2009-09-10
Hi guys. I am having some issues with performance of my RAID0/encryption/lvm.

I have successfully installed Jaunty on my system as per the tutorial I posted here:
[http://ubuntuforums.org/showpost.php?p=7874462&postcount=9](http://ubuntuforums.org/showpost.php?p=7874462&postcount=9)

I have noticed that the system is a bit sluggish compared to what I would have expected from a RAID0.

I have 5x Seagate Barracuda 1TB drives connected to Asus P6T Deluxe V2 motherboard. Ideally I would have set it up as fakeraid but I couldnt get it working because the 5TB fakeraid would never show up in the partition utility when I was installing from the alternate CD. Using smaller RAID volumes (eg less than 2GB) also didnt work as the installation failed after installer was unable  to continue.

Anyway, in the BIOS I set the controller to run the drives in AHCI mode and then set the drives up with a small /boot partition and a software RAID through the alternate CD. The RAID device is then used to create an encrypted volume. LVM is then used to create the logical volumes for root and swap within the encrypted volume. The installation went fine and I have had no problems with functionality at all.

The problem is drive speed.

------------------------------------------------------------------------------------

sudo hdparm -t /dev/sda1

results in

/dev/sda1:
 Timing buffered disk reads:  188 MB in  1.49 seconds = 125.94 MB/sec

------------------------------------------------------------------------------------

sudo hdparm -t /dev/mapper/lvm-root

results in

/dev/mapper/lvm-root:
 Timing buffered disk reads:  318 MB in  3.02 seconds = 105.45 MB/sec

------------------------------------------------------------------------------------

From the above, my understanding is that an individual drive is functioning faster than the RAID0 consisting of 5 drives!!!

I found some info earlier about readaheads and ran the relevant command to increase the LVM readahead. The information above is AFTER running even that. It was even slower before..

Any advice? Am I missing something basic? Any and all advice welcome :)

---

