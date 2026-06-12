---
title: "Why? Extended partition subject"
date: 2008-09-27
forum: General Help
---

### Post by melancholy00 on 2008-09-27
**Hi**

Only one question:

What is the advantage of having the Ubuntu OS and its Swap sharing the same Extended Partition? 

I have my Ubuntu OS in one primary partition and the Swap in the next adjacent primary partition.

Maybe my configuration isnt the best, because the use of a primary partition as a swap partition would be a waste of the limited number of primary partitions allowed.

---

### Post by dcstar on 2008-09-28
> **melancholy00 said:**
> **Hi**

Only one question:

What is the advantage of having the Ubuntu OS and its Swap sharing the same Extended Partition? 

I have my Ubuntu OS in one primary partition and the Swap in the next adjacent primary partition.

Maybe my configuration isnt the best, because the use of a primary partition as a swap partition would be a waste of the limited number of primary partitions allowed.

It doesn't really matter one way or the other.

The only issue will be with changing the Extended Partition, which will require all partitions inside it be unmounted if you ever want to resize it.

---

