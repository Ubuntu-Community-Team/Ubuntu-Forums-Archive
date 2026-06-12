---
title: "FakeRAID cache &amp; recovery options"
date: 2015-02-07
forum: Hardware
---

### Post by dsnc on 2015-02-07
Hi,

I'm getting ready to build a new system based on Ubuntu 14.04, and I have a couple of questions regarding Intel's "fakeRAID".  I'm planning to buy a motherboard with a Z97 chipset, and what I'd like to achieve is two RAID arrays: a RAID1 to store the operating system, and a RAID5 for data storage--photos, music, etc.  I've already got a SSD that I'd like to use as part of the RAID1 mirror, and several 1TB HDDs for the RAID5.  There are two questions that I'm trying to resolve: 1) If I use the SSD with a same-sized HDD in a RAID1 configuration, will the system be limited by the write performance of the HDD (or read performance, for that matter), and 2) what are the advantages/disadvantages to using software RAID for the data storage array?  From the research I've done I understand that one of the major advantages is that the disks can be moved to another system if necessary and the data can be recovered without loss, but the same is not true for an array built with the fakeRAID solution. If anyone with experience in this area could comment on either question or offer pointers to any docs, I'd really appreciate the help!

Thanks!

---

### Post by SeijiSensei on 2015-02-08
Don't bother with fake RAID.  Just use the software RAID that comes with the Linux kernel.

---

### Post by dsnc on 2015-02-08
Thanks for the help, SeijiSensei!  I've been under the impression that I can't boot the system from a software RAID mirror, though.  If I'm wrong that would be great--problem solved.  On the other hand, if the SSD were to fail I'd rather not have a system that I can't boot for a couple of days until I can replace it and restore from backup.  Does that make sense?

---

### Post by SeijiSensei on 2015-02-08
It's possible to boot from a software RAID device if you have the kernel properly configured.  The drivers have to be in initrd I believe, but I've never tried that.  I just boot from a normal partition and mount the RAID device later.  Usually I don't bother to use RAID for the system directories since I can just reinstall those.  I use RAID for more volatile storage like /home.

Aren't the chances of an SSD drive failing pretty low since they have no mechanical parts?

---

### Post by dsnc on 2015-03-26
Thank you for the help and sorry to take so long to respond.  I took your advice and dropped the idea of a RAID 1 mirror for the OS--reliability of a SSD and a good backup strategy make that a kind of outdated configuration, at least for a personal system.  Thanks again!

---

