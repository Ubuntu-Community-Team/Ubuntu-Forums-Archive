---
title: "Workaround for 4 Primary Partition Barrier?"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by kendoori on 2009-11-07
I am preparing to upgrade and want to move "Home" to a separate partition. My X61 laptop is dual boot, and my XP install remains intact on its own partition (sda2). I share data between XP via an NTFS partition that has "My Documents" on it (sda1). I then have another primary partition that is my current 9.04 install (sda3), and a Ubuntu swap (sda4) I've attached a screenshot of my current partitioning scheme.

I was prepared to shrink sda3 and use the unallocated space to create an sda5 that would be the landing place for Ubuntu "Home." When I fired up gparted from the LiveCD it informed me that I could only have 4 primary partitions (I guess swap is considered primary) and that I could potentially use extended partition but that I might need to delete a primary to do that.

Would appreciate if someone could help me think through how I can accomplish what I want to do without destroying any data (I do have good backups). Obviously I have plenty of room on my NTFS drive, so I could potentially break that into two logicals, but I'm not sure what the smoothest way of doing that would be.

---

### Post by josephe on 2009-11-10
Hi there

Almost my problem exactly, I also have 4 primary partitions. I'm wondering if I delete the swap partition. if Ubuntu create its own again? That way I can delete Swap, create a new logic partition on the free space I have, create the additional Primary i want in that and then boot Ubuntu and have it recreate swap. But I have no idea if this will work :-(

---

### Post by kendoori on 2009-11-10
I haven't implemented yet, but I think the trick here is to go for a swap file, not a swap partition. In my situation this would allow me to just delete the existing swap partition and convert/shrink/grow some available space into an additional primary or extended. See this FAQ: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

