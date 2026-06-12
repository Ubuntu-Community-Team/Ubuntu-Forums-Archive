---
title: "Can get all ext3 partitions to load cept Ubuntu"
date: 2008-11-07
forum: General Help
---

### Post by jorwex on 2008-11-07
Hey all,

Since about a week ago (actually...maybe it coincided with updating to Intrepid...) I haven't been able to get my Ubuntu partition to load in other OSs. This includes XP & Server 2008. However, my other two ext3 partitions for Documents & Storage work fine. 

I use the fs-driver.com ext3 driver (it may be ext2 and not support journaling...i forget) but use all of them as read only just in case. 

I like to send files between the different partitions, so it's a bit annoying. Gparted doesn't say there's an error or anything like that. I don't really know how to begin troubleshooting, as I don't get any error messages anywhere. It just doesn't mount when I load the OS.

Thanks,

Jordan

---

### Post by jorwex on 2008-11-08
ahA!

I think the problem arises from most ext2 drivers for other OSs work for only partitions with 128 Inodes. 

Intrepid changed to 256. Can I change the partition's inodes?

---

