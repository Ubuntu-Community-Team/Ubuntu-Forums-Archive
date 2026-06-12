---
title: "Should I partion large data drives?"
date: 2008-04-29
forum: Hardware
---

### Post by jrollf on 2008-04-29
I just ordered two 500GB WD SATA hard drives and a Syba SD-SATA-4P SATA PCI controller card for my home server.

Should I partition the drives? They both will be used only to store files on the file server (Ubuntu will be kept on the 30GB drive), I have no reason to do RAID as all the files already have backups in the form of CDs, DVDs, and other computers, and I prefer to have the extra storage vs. improved speed.

Would there be any performance or reliability improvement by partitioning the drives and making multiple smaller drives? I can't think of any, but I'm still fairly new to Linux so I thought I would ask. I use Samba to do the file sharing. I might run a mail server and/or personal ftp server in the future, and again, only the data/files will be stored on these drives, not the actual programs.

Thanks!

---

### Post by red_five on 2008-04-29
No, don't partition them. Create a LVM volume that spans both drives. It's not RAID, it's a single logical volume that spans multiple physical drives. It can be expanded later, too, if you get more drives. 2 500gig drives will give you nearly 1TB of storage, especially if you use XFS or ReiserFS (Hans' legal troubles notwithstanding).

---

