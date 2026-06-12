---
title: "Cannot install anything"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by nikolardo on 2009-05-29
This is a question aimed at any operating system in general with ubuntu specifics.
I recently came into possession of a Panasonic Toughbook CF-28.  It was from a state surplus auction, and before they auction off their stuff, they give it a good clean wipe.  Which means I have this laptop with no operating system, but that should not be a problem.
The thing is, there is no CD drive, and you can't boot from the USB port.
There is a CD drive listed in the BIOS, but it doesn't exist.  The USB port does not show up in the BIOS.
I have tried a number of different ways to get an operating installed.  I put a DSL floppy in the floppy drive which will let you boot from a CD drive not on the BIOS, but it didn't work for a USB cd.
I have attached the hard drive to various computers both by USB and internally and installed operating systems, mostly Ubuntu.  However, when the drive is put back in the Toughbook, it says "Multiple Active Partitions.  No Operating System found."

I came close to success when I made a USB bootable drive out of the hard drive (using the USB startup disk creator tool).  This will boot when in the Toughbook.  The first time I tried to install it, I found that I could not, as there was only the one partition, so I went back to my good laptop, shrunk the partition which was the USB install disk on the Toughbook's hard drive, and popped it back in.  Now, I can get all the way to the end of the installation, where it tells me
"The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted.
/cdrom"

It then offers to try again, with a "Go Back" and a "Continue" button.  Both buttons really lead back to the partitioning section of the install.
In the live USB environment, I found that the hard drive, at least the part with the Ubuntu USB formatting, is mounted at /cdrom and thus cannot be unmounted.  Is there any possible way to get an operating system on this computer?

---

