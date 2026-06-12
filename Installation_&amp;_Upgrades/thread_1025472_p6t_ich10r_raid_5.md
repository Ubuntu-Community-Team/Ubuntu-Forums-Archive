---
title: "p6t ich10r raid 5"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by ainacio on 2008-12-30
I am trying to install Ubuntu on a new computer.

- In BIOS, I configured SATA as RAID
- In the Intel Matrix Storage Manager, I made one Raid5 volume. 
- I booted from the Ubuntu CD, and during the installiation, it seems that it still recognizes three drives.
- How do I tell the Ubuntu setup that I have one RAID voulme? 


ps:
- I tried installing on one of the three drives. When I restarted, I recieved an 'error 2' GRUB message... in which case my system would hang.

---

### Post by dwarness on 2008-12-30
I too would like to see the answer to this.  Yes, I know Linux supports software raid, but I would like to use my ICH10R mirror as configured.

---

### Post by ainacio on 2008-12-30
Many people are claiming that the RAID controller which comes with the motherboard is a simple software implementation, which was designed to work nicely with Windows.

Since the box I am building will not have Windows installed, I have decided to use Linux's RAID software implementation. 

Here are the steps I used to get mine working... Keep in mind that I have 3 drives with T total bytes each.

1. Use the Alternate install CD
2. When we arrive at the Partition part of the setup, I partition the disks as follows:
  sda:
       50MB (With boot enabled) 
       2950MB SWAP
       70GB RAID
       remainder RAID
  sdb:
       3000MB SWAP
       70GB RAID
       remainder RAID
  sdc:
       3000MB SWAP
       70GB RAID
       remainder RAID

After the partitions were set, I used the 'configure RAID' option to make one RAID0 (using the 3 70s), and one RAID5, using the 3 remainders.

We made a 50mb boot partition because the boot program will not boot from a software RAID configuration. 

After the RAID was configured, I set the RAID0 configuration to my / mount, and the RAID5 to my /home.

---

### Post by Charlie708 on 2008-12-31
Have you installed dmraid?

---

### Post by OmnyDevi on 2008-12-31
[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

That is the best link I have seen. I have been trying to install with raid0 for a while now, but grub seems to hate it. Might say screw it and try a raid5 later this weekend. Sure would be nice to have a raid0 though :(

---

### Post by OmnyDevi on 2008-12-31
[QUOTE=ainacio;6464613]Ma

We made a 50mb boot partition because the boot program will not boot from a software RAID configuration. 

QUOTE]

Was the Boot partition on the raid? Or a seperate hard drive?

---

### Post by ainacio on 2008-12-31
> **OmnyDevi said:**
> 

QUOTE]

Was the Boot partition on the raid? Or a seperate hard drive?

I have three hard drives. In the first drive, I allocated 50mb for booting. I allocated swap on each drive, and made the swap on the first drive 50mb smaller so the drives would all be equal size again. I made both a RAID 5 and RAID 0 configuration, for the important data and replacable data respectivly.

---

### Post by rjsherman1 on 2010-10-21
Okay ... so I'm trying to install ubuntu 10.10 desktop to an older Intel box ... has an ICH7 controller and have a RAID5 array configured on this box.

Ubuntu installer detects this array as a single device ... installer runs, appears to complete properly but upon restart the system responds with no boot device detected ...

um ... wow ...

pointers ?  please ?

I'm pretty darn new to installing any variation of Linux -

---

