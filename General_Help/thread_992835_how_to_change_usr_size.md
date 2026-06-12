---
title: "how to change /usr size?"
date: 2008-11-25
forum: General Help
---

### Post by camotito on 2008-11-25
Hello,

I decided to try new things during a recent installation of Linux. I just created new partitions to /home , /usr , /tmp , etc.
I allowed 2 GB to /usr. I was not sure of this and now I see that it was a mistake because I don't have enough space to install VMware Server. 
How can I change the size of the partition I created and solve this so I don't have future problems when installing new things?
I don't have any idea where to go now. I don't need detailed explanations but some hint where to go or what to read.
Thnks!

Javi

---

### Post by Elfy on 2008-11-25
Should be able to use the partition editor on the livecd to do that - you'll likely need to shrink and move other partitions so that the free space is next to /usr

After you've done - check that the partitions UUIDs are reflected in fstab - they could have changed.

---

### Post by binbash on 2008-11-25
you can resize the partition via Gparted live cd

---

