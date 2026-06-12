---
title: "Raid in Ubuntu"
date: 2008-10-03
forum: Hardware
---

### Post by gtno on 2008-10-03
Hello,

I am quite new to Ubuntu and I was reading a few threads on how to install a Raid, but I am unsure of how to do it still.  The raid drives are NTFS and have data already on them, and I just wanted to mount the raid.  I installed a NTFS Configuration Tool to mount my drives and all of them were mounted except my raid drives.  I am unsure of the device location of these drives as well.

My motherboard is the following:

MSI P6N SLI Platinum LGA 775 NVIDIA nForce 650i SLI ATX Intel Motherboard

and the Hard Drives are the following:

2x Western Digital Caviar SE WD2000JS 200GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM

Any advice or a great step by step tutorial would be greatly appreciated as I am still searching for my answer. Thanks in advanced.

---

### Post by cariboo on 2008-10-03
The first thing we need to know is if you have an onboard raid chip. If you do then checkout this howto:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

If you are using an addon raid adapter, we will need to know the make and model.

Jim

---

### Post by gtno on 2008-10-03
I am using onboard raid chip.  I was following the instructions to the FakeRaid HowTo, but I got stuck at a certain point. I got dmraid installed and when I entered the command "sudo dmraid -ay" I got the following:

RAID set "nvidia_iadeabha" already active
RAID set "nvidia_iadeabha1" already active

Then the HowTo went into wanting to partition the drive etc., but I was trying to figure out how to mount the raid, I don't want to partition it or anything... as I have information on the drive that I wish to keep.  So, I typed "sudo dmraid -r" and I recieved the following:

/dev/sdd: nvidia, "nvidia_iadeabha", stripe, ok, 390721966 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_iadeabha", stripe, ok, 390721966 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_jjfcabej", stripe, ok, 488397166 sectors, data@ 0

I need to mount the /dev/sdd and /dev/sdc as a raid, how do I do that?

---

