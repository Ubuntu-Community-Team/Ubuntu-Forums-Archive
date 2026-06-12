---
title: "Partition problems on macbook"
date: 2010-10-13
forum: Hardware
---

### Post by ncubani on 2010-10-13
I have a macbook 13" and installed Ubuntu 10.10 alongside mac OSX. I first created a separate partition with Oriolos, after which I installed reFit. Then I boot into the live CD (Ubuntu 10.10), after which I installed Ubuntu straight to the new partition. {I am impressed with the new installation menu on 10.10 which allowed me to format and allocate the new partition to Ubuntu during the installation process}. However, I also had to assign a swap partition, and I think this is where things went awry. When I boot, reFit launches first. Then when I select the linux icon, I get to the boot section of Ubuntu. However when I press "enter" on the top line, nothing happens.
I booted into the live cd again and have the following information after launching gparted: [ps. I have no technical background on linux, try things here and there after reading on the various forums].
 
_Partition    - File System - Label    - Size    - Used      - Unused - Flags_
/dev/sda1 - fat32          - EFI       - 200Mb - 22.18Mb - 177Mb   - boot
/dev/sda2 - hfs+           - Mac HD - 71.4Gb- 50.3Gb  - 21.16Gb - 
/dev/sda4 - linux-swap  -             - 127Mb -     0       -   0         - 
/dev/sda3 - ext3           -             - 40.01Gb- 3.14Gb - 36.87Gb -    -----> this is the partition on which Ubuntu resides.
 
Million dollar question: How can I correct this problem? Is ithe order of the partitions ok? (4 before 3)...etc
My macbook has a 160Gb harddrive and 2Gb of memory. (2009 model)

---

