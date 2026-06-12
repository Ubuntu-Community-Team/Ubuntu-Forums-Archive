---
title: "New &quot;old&quot; hard disk won't format"
date: 2020-12-19
forum: Hardware
---

### Post by michael351 on 2020-12-19
I bought a tested as good hard drive 4TB (WD) for use in my Ubuntu desktop. The drive won't initialize or format and shows read errors whether I use Gparted or fdisk. The OS does show it to be a WD 4TB drive with appropriate serial number.

I installed the drive on a windows machine and I was able to initialize, format and assign a drive letter and volume label straight away (GPT / NTFS)
When I re-installed this drive back on my Ubuntu machine, same problem. I can't use this drive.

I am wondering if it could be the connections? I am using a WD Elements enclosure which housed my 2TB drive this one is replacing. 

Any ideas?

---

### Post by CelticWarrior on 2020-12-19
Are you sure the enclosure supports drives of that capacity?

---

### Post by michael351 on 2020-12-19
Actually - no. The fact it worked on a windows machine (w/ standard sata & power) tells me that's probably the issue.

---

### Post by rsteinmetz70112 on 2020-12-20
Are Windows and Ubuntu on the same hardware? It sounds like they are on different computers.

---

### Post by CelticWarrior on 2020-12-20
I suggest you try it in the enclosure and connected to the Windows PC. If the behavior is the same that rules out the OS and directly points to the enclosure.

Most enclosures from ~7 years ago or older supported up to 2TB drives.

---

