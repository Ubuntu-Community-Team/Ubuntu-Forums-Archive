---
title: "RAID Troubles with WD EADS Green Drives"
date: 2010-10-23
forum: Hardware
---

### Post by mehstg on 2010-10-23
Hey guys

Sorry if I am posting in the wrong section!

Basically, I am trying to install Ubuntu Server 32bit on a box I am running at home. I have tried 10.4 LTS and 10.10 and always hit the same problem.

The system has four disks, shown as follows:

80gb Hitachi Deskstar - System Drive
3x Western Digital Green WD15EADS

Two of these EADS drives are EADS-00p, and one is an EADS-00s. They were all purchased at the same time, unfortunately, I did not realise one was different at the time!

I am having issues with my MDADM software raid in the setup process. All four drives show in the partitioning wizard, however after assigning a RAID partition to all three 1.5tb drives, when I go into the create MD device menu, the EADS-00s does not show. Initially, I thought this could be down to a dodgy SATA cable or SATA port, but changing the port the drive is on changes nothing, the 00p disk still does not show up. 

Any ideas on what could be causing this.

P

---

