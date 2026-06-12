---
title: "'Starting up partitioner' freezes during Ubuntu Server install"
date: 2011-09-30
forum: Hardware
---

### Post by lorewap3 on 2011-09-30
Here's my hardware:

GA-880GA-UD3H(rev. 2.2)
[http://www.gigabyte.com/products/product-page.aspx?pid=3789#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3789#sp)


Had Ubuntu 11.04 server running with 6 Seagate 1TB ST31000524AS drives. Was NOT using the 2 white gigabyte sata ports, only blue. (8 sata ports total on MB)
1x IDE DVD-ROM (For Ubuntu Server Install disk)

I was trying to upgrade to use all SATA slots.
4 x Seagate 1 TB ST31000524AS in blue sata slots.
-----     [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148697](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148697)
2 x Seagate XT 2 TB ST32000641AS in blue sata slots.
-----     [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148506](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148506)
2 x Seagate Green 2TB ST2000DL003 in remaining 2 white sata slots.
-----     [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148681](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148681)

I've tried setting both SATA chipsets to AHCI, to RAID (with no RAID setup), to IDE.

I don't want a hardware raid, I want to setup a software raid using LVM so I can expand/reduce drives with much more ease and flexibility than a hardware raid would allow.

As the title says, the installer works fines and the hardware RAIDS see all the drives just fine. It's when it gets to "Starting up Partitioner" that is just freezes at 37%.

I am open to ANY suggestions. I have changed every BIOS setting related to SATA that I can think of, yet it still freezes there.

A very important piece to note, however, is that the 4 x 1TB drives that are still hooked in still have the old partitions in them. I have tried to boot Gparted to format them but even that freezes and never gives me a hard drive list to format that. I've considered that 'might' be the problem, but then why would a program designed for formatting drives freeze as well? Any clues at all where to go from here would be so very much appreciated!

---

