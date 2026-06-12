---
title: "U Server 10.10 - Hard drive not recognized"
date: 2011-03-23
forum: Hardware
---

### Post by Wug on 2011-03-23
I have Ubuntu server installed on a WD 1TB drive.
I have Windows 7 installed on another WD 1TB drive.

The Ubuntu drive has 3 partitions - ext4 system (~190GB), swap (~8GB), ntfs data (~730GB)
The Windows drive has 2 partitions - ntfs system (~100GB), ntfs data (~830GB)

I have an Asus P6X58D-E motherboard
The Windows drive is connected to a SATA 6Gb/s port, and the Ubuntu drive is connected to a 3Gb/s port.  I can see both drives from windows, but I can only see the Ubuntu drive from Ubuntu.  I will try different sata ports and see if it has something to do with the SATA 6Gb/s.  I will also try alternate bios configurations to see if there something amiss there.

---

### Post by Wug on 2011-03-23
Playing with settings, it definitely seems like an issue with the Sata 6Gb/s ports.  I moved the ubuntu drive to a 6Gb/s port, and it was unable to boot (gave up waiting for root device)

Is there some way I can configure it to recognize the 6Gb/s ports?  I can't move windows to a 3Gb/s port because like linux, it fails to boot if I switch it.

The solution seems to be to make linux recognize the other drive.   How would I do that?  The p6x58d-e uses a marvell sata 6Gb/s controller.  How would I go about finding drivers for in on linux?  It's a reasonably common motherboard so I'd think that this issue would've come up in the past sometime.

---

