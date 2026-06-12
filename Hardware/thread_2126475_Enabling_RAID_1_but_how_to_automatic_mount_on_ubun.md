---
title: "Enabling RAID 1 but how to automatic mount on ubuntu"
date: 2013-03-17
forum: Hardware
---

### Post by whitefish10 on 2013-03-17
Hi guys, I have three hard drives. And I have enabled RAID 1 on only two of them using the motherboard (hardware raid 1). 

What I want is to install ubuntu on the last drive and mount the drives from there. but it seems that ubuntu didnt do it it. Please adivse me.

thanks,

---

### Post by TheFu on 2013-03-17
Motherboard RAID is known as "Fake-RAID" because it usually requires specific drivers to be loaded into the OS running to be used.  Google will teach you more about it.  Performance of FakeRAID tends to suck when compared with a real RAID card that has everything built into hardware - 3Ware is an example vendor.  Only true hardware RAID cards that are configured before any OS is booted can be used with Linux unless drivers are available for your specific Linux kernel (and updated kernels).  I have a real-RAID card, but elect to use softRAID for the added flexibility.

Most Linux users decide that the use of the excellent software RAID provided in almost every distro does the job, provides greater flexibility and your data will not be locked up due to a MB or other hardware failure.  I've migrated softRAID partitions across 3 different physical systems - no issues at all.  At work, we've been stuck trying to find an exact matching RAID card 5 yrs after EOL just to get access to our data again - eBay was NOT our friend.  We ended up accepting 20 hrs of data loss and restoring from backups.

Google for "ubuntu software raid" to learn about **mdadm** so you can setup your softRAID. There are a few how-to guides out there.  mdadm has been extremely stable for me the last 8+ yrs. It is easy to use and with modern CPUs, very fast.

---

