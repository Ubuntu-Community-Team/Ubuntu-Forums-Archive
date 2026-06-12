---
title: "Mounting a RAID-5 XFS File system"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by advnet on 2008-01-02
I have a Buffalo Technology TerraStation, which is a one terabyte NAS Device that is on a unix based platform. The motherboard and/or Firmware has gone out on this device with important data on the drives. I am wanting to know if it is possible and if so how to remove the 4 hard drives from the TeraStation and mount them on a PC running Ubuntu Live from a CD. These hard drives are running as a RAID - 5 and are formatted with the XFS file system. My goal in doing this is to fully recover all inaccessable data on these drives and copy them to another storage solution so they can be used again on the new server. If anyone could lend me a helping hand with this I would greatly appreciate it.

Thank You,
Ryan Durbin
System Administrator
Advanced Networking
[email]rdurbin@advnetworking.com[/email]

---

### Post by samosamo on 2008-01-05
I wouldn't even attempt this without backing up the data first.  And since the data is backed up, you won't have a problem transferring it to your Ubuntu box.  right?  right.

edit: i just read that the box is fried.  that sucks.  um, what you said won't work unless the terastation uses linux raid which i doubt.  it probably uses some kind of proprietary softraid.  if i'm wrong, you're lucky, but if i'm right the only way to get your data back is to call Buffalo for replacement parts.

---

