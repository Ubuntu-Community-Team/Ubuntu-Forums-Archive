---
title: "Cannot create more than one extended partition?"
date: 2010-04-26
forum: Hardware
---

### Post by x-shaney-x on 2010-04-26
I am wanting to format my partition like this:

Primary - Windows
Extended - 3 linux partitions + swap partition
Extended - 2 data partitions

I'm using gparted and have created the primary and first extended partition with no problems but I am unable to create another extended partition with the remaining space.
It is only allowing another primary.

Thing is, before I wiped the drive, it was setup exactly as above.

---

### Post by x-shaney-x on 2010-04-26
Well it seems I may be mistaken since the gparted documentation states that you can't have more than one extended partition.

So if I did it like this:

Primary - Windows
Primary - Data 1
Primary - Data 2
Extended - Linux

Would that be too much and is the any performance difference between having your main OS parition at the beginning or near the end of the drive?

---

### Post by mikewhatever on 2010-04-26
Why did you want two extended partitions? As far as I can see, you can have one primary partition for Windows, another extended one, and within that, logical partitions for the rest.

---

### Post by x-shaney-x on 2010-04-26
More than anything else, I just wanted the data keeping completely separate from the os partitions.

I haven't played around with distros for a while but I'm about to and I thought having them on a separate extended partition would give a visually clear indication of where they are when it comes to partitioning and deciding where to install when installing new distros.

Now I think about it, it is pretty pointless really.
I'm going to stick to one primary and one extended, which is how I must have had it before (really there were so many partitions it was hard to remember).

Still curious about whether it makes a difference if the OS is at beginning or near end of drive though.

---

### Post by mikewhatever on 2010-04-26
The angular velocity of a spinning disk is greater at its edges and gets lower towards the center, which means the beginning is faster. Not that you notice it.

---

### Post by i.r.id10t on 2010-04-26
Only one extended partition (and it must be a primary) and then logical partitions inside of the extended partition.

---

