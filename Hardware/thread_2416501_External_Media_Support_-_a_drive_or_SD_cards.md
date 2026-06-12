---
title: "External Media Support - a drive or SD cards"
date: 2019-04-10
forum: Hardware
---

### Post by basicsearcher on 2019-04-10
I am a current user of Ubuntu 10.04 LTS, planning to instal 10:18 MATE and as part of this, need to increase external storage.
Media could be an external drive, or SD cards.
My question is about support for the following product:
"WD Elements 1TB Portable Hard Drive
Formatted NTFS for Windows 10, Windows 8.1 & Windows 7.
For Mac OS X reformatting will be required.
OS Required Apple MacOS X, Microsoft Windows 7 / 8.1 / 10"
My hardware is dedicated to one Ubuntu MATE OS:
Sony VAIO laptop VPCEB1EOE - several years old, with legacy BIOS
My first question is whether I am posting into the right forum category.
My second question - what more information need i supply, as this is just basic data to introduce the subject.
I should add that at 77 I am still very much a Linux newbie, so can use the terminal for simple tasks. That's about it!
Thank you in advance for your guidance.
Patrick

---

### Post by Dennis N on 2019-04-10
All the WD external drives I have work fine with Linux. One is a 1 TB WD Elements Drive I use for archiving media, but it is several years old. The model number is WD 10000EB035-1. The command parted -l identifies it as WD 10EADS - which is the internal drive inside. 

To use it, I made a new partition table with gparted, and one big ext4 partition for my archive folders. 

With ext4, after partitioning, you will need to change the owner of the ext4 filesystem to your user so you get full access to your drive.

I also have 2 smaller WD Passports (250 gB) that were left as FAT drives (the default formatting). Also several years old.

---

### Post by Autodave on 2019-04-11
Are you really using version 10.04?  If so, you need to stop using that and get a newer version since that is very old and no longer supported.

Every 2 years, a long term service release is made.  18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.

---

### Post by basicsearcher on 2019-04-14
Thanks Dennis N. That's encouraging. Hope to follow your sucess.

---

### Post by basicsearcher on 2019-04-14
Hi Autodave. I messed up, my current Ubuntu OS is this one: Release 18.04.2 LTS (Bionic Beaver) 64-bit
I got confused, i guess, with Ubuntu OS, MATE release level: MATE 1.20.1, and Linux kernel no. Kernel Linux 4.15.0-47-generic x86_64.
BTW, I left off some key basic data in my original post. The laptop has: RAM 5.5 GiB, hard drive 320GB.

Thanks for the reality check!

Patrick

---

