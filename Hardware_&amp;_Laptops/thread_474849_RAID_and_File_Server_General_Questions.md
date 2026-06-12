---
title: "RAID and File Server General Questions"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by jmoesch on 2007-06-15
I am setting up a Linux file server at our small office (4 workstations) to replace a Windows XP box that is currently doing that job while also being my desktop computer.  The Windows box is running “fake RAID 1” and has been doing a fine job storing our documents, spreadsheets, accounting files, etc.  The goals are to:

1)	Gain somewhat faster file access on a dedicated machine
2)	Keep or improve the RAID redundancy 
3)	Allow easier and more automatic off-site backups
4)	Allow migration to open-source SQL database applications going forward
5)	Allow better secure access to needed files from home or the road

A little downtime now and then is not a big problem, but we don’t ever want to lose data.  

I concluded that we don’t need the increased speed of RAID 5, rather we just need the redundancy of RAID 1.  We setup an old box running Smoothwall (a Linux-based firewall) to securely allow offsite access and that is working great.  We can access the Windows server from offsite; using VNC I can email myself any needed files and even encrypt them before sending, though I’m sure there are more elegant solutions especially once we get the Linux file server going.  We bought a MSI 915G Neo2 motherboard with 1mb RAM and a Celeron 2.66.  It can run 4 SATA drives or 2 PATA drives, and we put it in a big rackmount case.  Also picked up an external Seagate drive ($50 for 150gb!) to use for on-site backups connected to another machine and I will install a UPS on the new Linux server just so it can shutdown without data loss and to act as a big surge protector.  

My thought is to buy three identical drives and run two of them RAID 1 with the third as a cold spare.  My question is: will Linux be able to run software RAID 1 with SATA drives (Intel 915G+ICH6R chipset) or will I need to use PATA or should I chuck the fake RAID and go with real hardware RAID instead?  Since I am running a low-intensity server here, is there any reason to go with the “Server” edition of Ubuntu since I’m not exactly a Linux guru and the graphical interface might be easier (I have set up a practice server following [this]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html") excellent tutorial)  I’ve read that the normal desktop version can be a LAMP server too (some of the SQL applications I’m thinking of trying need a LAMP server – we are not going to host a website!).  

Any other thoughts on how to make this system come together would be greatly appreciated.  Thanks in advance.

---

### Post by disasm on 2007-06-15
Software raid works great with ubuntu. I have a raid 5 with 4 250G disks in my server using mdadm. Was a piece of cake to setup as well.

Sam

---

### Post by jmoesch on 2007-06-16
> **disasm said:**
> Software raid works great with ubuntu. I have a raid 5 with 4 250G disks in my server using mdadm. Was a piece of cake to setup as well.

Are you using SATA disks?

---

### Post by disasm on 2007-06-18
yes, ahci module iirc.

Sam

---

