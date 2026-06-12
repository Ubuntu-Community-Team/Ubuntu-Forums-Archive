---
title: "New system dual boot ubuntu/win7 partition advice"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by scottyab on 2009-06-01
Hi, 

I'm building a new system and planning to dual boot ubuntu 9.04/Win7. I'm pretty sure ubuntu will be my main os for the future, but concerned about potential hardware issues, hence the dual booting. I'm not a PC gamer and mainly run loads of applications, IDE's, web browsers, etc 

Currently I have a new 1TB drive and wondered how it's best to partition it?

I was thinking... 
80GB NTFS for Win7
80GB Ext3 for Ubuntu
4GB Swap
Rest for Data/Photos/Music/Video/Vm

That seem reasonable? I'm planning to use the gparted partition tool to create the partitions. 

Thanks, 

Scott

---

### Post by lake54 on 2009-06-01
I'd be tempted to make the OS partitions 100 each, 'just in case'.

Also you may want to invest in another HDD for a backup - would be a shame to lose 2 OS's and a bunch of data. You could also try RAID - i.e. mirroring one drive onto the other.

HDDs are pretty cheap these days - SATA is cheaper than IDE as well.

James

---

### Post by Mark Phelps on 2009-06-01
> **scottyab said:**
> I was thinking... 
80GB NTFS for Win7
80GB Ext3 for Ubuntu
4GB Swap
Rest for Data/Photos/Music/Video/Vm

That seem reasonable? I'm planning to use the gparted partition tool to create the partitions. 

Windows 7 appears to use significantly less disk space than did Vista, so 80GB is a LOT of space, especially if you're planning on having a shared drive for holding most of your data.  You should be able to get by easily with half of that for Seven.  You could make it 50GB if you want spare room.

Ubuntu uses even less space.  I've had a 30GB partition for years now, upgraded again and again, and I'm hard pressed to use up over 5GB.  So, I would chop that back to 10GB.

As to the shared partition, format it NTFS and be sure to include the ntfs-3g and ntfsprogs packages in your Ubuntu install. With those, you'll have no problems sharing the NTFS partition with Seven.

---

