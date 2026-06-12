---
title: "Setting up a hard-drive array on ubuntu 12.04"
date: 2012-12-12
forum: Hardware
---

### Post by BavidDowman on 2012-12-12
Hi all,
I recently bought this hard-drive array  [https://eproc.scw.com/s/?i=S8932299](https://eproc.scw.com/s/?i=S8932299)

Like most hard drives that can be purchased online, this one too is recommend for Mac/Windows only. 
Now I have purchased hard-drives in the past, and in most cases  I just reformatted them to ext4 before first use.

Here, I have a different problem. This drive comes with "RAID ( Serial ATA-300 ) - RAID 0, 3, 5, 10, 5 hot spare".  I am guessing the particular type of raid will need to be set up. 

Here is my dilemma: I am use the provided driver CD, hook up the drive to a windows/mac, and configure the storage controller (e.g., to RAID 5). I can then try to have Ubuntu read and write to the ntfs/hfs filesystem (will redundancy of storage be maintained in that case?). Alternatively, I can reformat the entire drive and then setup software raid on it. But once I have reformatted the disk I don't think I'll be eligible for any support from the manufacturer.
 
I intend to store critical data on this drive so I want to be absolutely sure of what I am doing. I'll prefer to have RAID, just for the redundancy. 

Looking for advice.

---

### Post by dannyboy79 on 2012-12-12
will you have a mac or windows computer always around to manage the drive thru its cd installed software? I would say if not, then go ahead and format it and use linux software raid, mdadm. just my 2 cents

---

### Post by BavidDowman on 2012-12-18
My question is, is Hardware raid dependent on firmware for operation? This drive array has a *physically* switchable raid0,raid5, raid10... series of modes. How can I find if Ubuntu will identify this hardware?

---

### Post by dannyboy79 on 2012-12-18
ubuntu will be able to read/write from it but it won't be able to administer it AFAIK.

---

