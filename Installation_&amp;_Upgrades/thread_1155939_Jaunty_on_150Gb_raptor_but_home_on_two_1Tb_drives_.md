---
title: "Jaunty on 150Gb raptor but /home on two 1Tb drives in RAID1"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Fredvs79 on 2009-05-11
Hi helper folks,


 I'd like to create a new system from scratch. The hardware I'd like to use would be to run linux from a 150Gb SATA drive (WD Raptor) and store my home partition on another separate 1Tb SATA drive which will be mirrored on a third 1Tb SATA drive. The reason for doing this is that most of the programs and such I want to load quickly, while all my documents and such I want backed up.

My motherboard claims to support Raid 0,1,5,JBOD, but I read over here on [FakeRAID]("https://help.ubuntu.com/community/FakeRaidHowto") that this is not true raid: it is a multi-channel disk controller that runs through the BIOS with certain drivers to help the OS boot from a raid device.

Since linux has built in softRAID support, I was going to skip configuring the motherboard RAID support, but I wanted to know if I could get some help setting up the RAID in linux and how I should proceed through the setup wizard when installing linux, e.g. an order of operations such as (example, not sure if its right)

1) during install denote the / partition will be on the 150gb drive
2) denote the /home partition will be on the 1Tb drive
3) install
4) configure softRAID to mirror the 1Tb drive on the second 1Tb drive.

-OR-

2) during install denote that the 2nd and 3rd drives will be mirrored in RAID1??
4) no step 4, already completed during the OS install

 Any help would be appreciated.

---

