---
title: "Partition/Raid help requested"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by dralcohen on 2009-07-25
(Also posted under general. I apologize for the double post.)

I am awaiting the arrival of a new computer (some specs provided below). It will come with MS Vista installed. I would like to dual boot with Ubuntu. I would very much appreciate some advice on how to set up the system.

The computer is for work and play. The Vista is pretty much for gaming and a few proprietary apps. The Ubuntu will be used for the following:

Long computational jobs (number crunching)
Office work (documents, spreadsheets, etc)
Small application development (in Python)
Data analysis (statistics, etc)
Standard internet use (mail, web browsing, etc)
Music/photo/data storage (lots)
Quite a few non-distribution apps will be added (on the order of 15-30)

There will only probably be 1 or 2 user accounts.

I am planning on using the 2nd drive as a backup drive. Ideally, this drive would be an identical copy of the first. That is, if the first fails, I could swap them and have a bootable copy of my first drive. 

Here is my question: How should I repartition the drive and set up the system to best meet my needs and goals?

Repartition:

I haven't decided on the exact space I'm giving to Vista, but lets say 100GB. What partitions and what sizes (I'm very confused about sizes) for Ubuntu? I'm thinking as a minimum I should have /, /boot (for the dual boot), /home, and /swap. Given the number of non-distro apps I'll be using, should I include a /usr/local partition? If so, is a /usr partition suggested? Would a /tmp partition help with the computational jobs? File system types and sizes and partition types (primary, etc) would be great. 

Backup:

Someone suggested I look into setting up the drives as a Raid 1. Is this doable with a dual boot? If so, would that make a copy of drive 1 on drive 2 whether I'm in Vista or Ubuntu? If not, is there a way to do that? Do I need to make any special partitions for Raid to work? Is there a good step-by-step setup guide for Raid (or whatever backup system people suggest)?

Note: I am not afraid of computers, but I am VERY new to linux (I barely understood what I typed above), so step-by-step instructions and small words would be much appreciated :smile:.

Thanks in advance.

-----------------------------------------
System specs

Motherboard     EVGA X58 based chipset with DDR3, PCI Express, 3-way SLI!
Processor     Intel® Core™ i7 processor i7-920, quad 2.66GHz cores, 8MB Cache, 4.8 GT/sec       
DDR3 Memory     6GB DDR3-1333 Triple Channel Premium Memory with Heat Spreader (3x204)
PCX Video     1GB Radeon HD 4890 GDDR5, PCI-Express
Hard Drive 1     1TB Hitachi 7200rpm 16MB Cache SATA 300 w/NCQ       
Hard Drive 2     1TB Hitachi 7200rpm 16MB Cache SATA 300 w/NCQ 
Operating System     Genuine Microsoft® Windows® Vista Home Premium 64-bit SP 1

---

