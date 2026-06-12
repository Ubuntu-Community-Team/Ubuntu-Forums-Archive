---
title: "Adding a software raid after installation"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by DanishKiwi on 2009-10-24
Hi, 

I have just finished installing my first Ubuntu 9.0.4 desktop. It is primarily going to be used as a file server in our home network, for which reason I have purchased a couple of disks aI would like to setup in a RAID 1.

The system:
Atom based Intel MB, 2 GB RAM, 1 * 500 GB HDD (IDE), 2 * 1 TB HDD (SATA). 

The status:
The Ubuntu desktop 9.0.4 is installed and updated onto the 500 GB IDE HDD.

What I want:
I would like to install a software RAID (RAID 1) using the two 1 TB HDD. But I am having some issues. I have tried most of the things that I could find on the web, but they all cover installing the RAID duing OS install - and I am beyound that point.

 - I have the "alternate" install CD - tried it but no success
- I have tried the mdadm things - the /dev/md0 was there, but dissapeared after reboot.

The RAID should probably have FAT32 on it as windows based PC's will be using the files.

Any clues/ideas/solutions?

---

### Post by Rune Hagen on 2009-10-29
Install 0910 or 0910 RC,
Install mdadm
run 'system -> administration -> disk utility', 
In disk utility
file -> new -> Software raid

Working on it right now, for a home file server

---

