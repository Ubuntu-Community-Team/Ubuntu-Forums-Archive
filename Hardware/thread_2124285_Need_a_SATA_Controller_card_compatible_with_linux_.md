---
title: "Need a SATA Controller card compatible with linux 3.5"
date: 2013-03-10
forum: Hardware
---

### Post by Rhiadon on 2013-03-10
I purchased a Highpoint RocketRaid 620 because it was cheap and the reviews seemed ok. I cannot manage to get it to work. I've followed the guide here: [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid) 

I made the "appropriate" modifications to the patches to work with kernel version 3.5 but the module will not load fully. The command "modprobe rr62x" starts to work, get a few messages in dmesg but it never finishes. The modprobe actually just hangs.

So what I'm wondering is are there any SATA controllers that are known to work in kernel 3.5? I've done quite a bit of searching to no avail. My google-fu is not the best, admitedly. I don't want to use any RAID functionality in the card as I plan to do software RAID with the card. Just looking for something cheap that isn't slow as a dog. Two WD 2TB Red drives will be connected to it.

Barring that, has anyone got the RocketRaid 620 working with kernel 3.5? If so, how? Can you send me your kernel module rr62x.ko?

---

### Post by dabl on 2013-03-10
I can't testify about the "kernel 3.5 support" requirement (you can check that issue), but here is a vendor of known good quality, Linux supported RAID controllers:  [http://www.3ware.com/products/serial_ata.asp](http://www.3ware.com/products/serial_ata.asp)

As an alternative, and assuming that you will be using the RAID array for data and not your OS, you might want to take a look at installing a BTRFS filesystem on the two (unformatted, no partition table) drives.  I have been running a pair of WD1002-FAEX drives in that configuration, on a SATA 3 controller, for 2 years with no issues.  In the default configuration, metadata are mirrored, and data are striped.  More here: [https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

Note that BTRFS is relatively new and still categorized as "experimental", although my own experience matches the claim of the BTRFS developers: "BTRFS is stable on a stable system."

---

### Post by Rhiadon on 2013-03-10
Thank you very much for taking the time to give me some advice. I looked at the cheapest 3ware device and that's way salty. And it's a hardware RAID card.

A little more information on what I'm doing: I'm building a FreeNAS system using the 5 WD 2TB Reds using RAID Z2. So it's software RAID. The kicker is that the FreeNAS system is running in a KVM virtual machine with direct access to the 5 disks. But I'm out of SATA Ports, so I just need a cheap set of ports. Hence why I went with a cheapo software RAID card because I had no intention of using the RAID capabilities of the card.

I do greatly appreciate you taking the time though.

Any others have some help?

---

