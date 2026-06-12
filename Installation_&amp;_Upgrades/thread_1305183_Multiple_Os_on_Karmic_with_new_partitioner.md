---
title: "Multiple Os on Karmic with new partitioner"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by darnanthony on 2009-10-29
Multiple Os on Karmic with new partitioner
Hello,

I currently have 64-Bit machine that has a 250 GB SATA drive that has three primary partitions and a extended partition. The three primary partitions sda1, sda2, and sda3 are 20.5 GB each and have jaunty 64-bit, hardy 32-bit, and windows 7 RC Os installed previously on them, respectively. The extended partition (sda4) is about 171.7 GB and is divided uniformly and consecutively as follows:

sda9 4GB Linux swap
sda10 12GB NTFS --used
sda11 25GB ext3 ---> empty partition I wish to place the new Karmic 64-bit OS
sda5 33.2GB NTFS --used
sda6 34.5 GB NTFS --used
sda7 34.7 GB NTFS -- used
sda8 28.3 GB NTFS --used

My question is if I try to install the Karmic 64-Bit OS on the above empty partition, will the new partitioner install a grub boot menu that will recognize all the other operating systems? If not, what is the best way to install it to allow all of them to be recognized at boot menu? How can I use the manual partitioner so that all of them are recognized.

I tried to install Karmic in the above manner. When I got to the partitioning screen, it showed all of the other other systems and had the radio button filled ["install side by side"] but did not instruct me on where to install the OS. When I pressed the option to go to the next screen, I received the message "Everything will be deleted."


Thanks, DA

---

