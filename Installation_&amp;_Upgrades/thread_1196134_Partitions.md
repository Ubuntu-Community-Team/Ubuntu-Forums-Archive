---
title: "Partitions"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by MartinEve on 2009-06-24
Hi all,

I am somewhat confused about my current partition setup.

I initially installed through wubi, but then used the Loopmounted Virtual Partition Manager to move wubi to its own partition.

I've now thrived on my Ubuntu setup for 6 months without a single Windows boot and want to move full-time (ie. getting rid of my ntfs partition)

Here's the layout of my system drive:

[[IMG]http://img149.imageshack.us/img149/6572/partitions.th.png[/IMG]](http://img149.imageshack.us/i/partitions.png/)

It seems that the Linux partitions are both extended. How, therefore, is it possible that I am booting from them? I thought you could only boot from a primary partition...

Also: can I make this partition primary using GParted? If not, what would be the best strategy for getting the partitions sorted out without losing any of my setup?

Thanks in advance,

Martin

---

### Post by mk1w86 on 2009-06-24
Ubuntu uses the grub boot loader (usually residing on the MBR) which can boot extended partitions.

> Also: can I make this partition primary using GParted? If not, what would be the best strategy for getting the partitions sorted out without losing any of my setup?

Your partitions seem fine therefore I would not make any changes to them.

---

### Post by presence1960 on 2009-06-24
welcome to linux. Linux will boot from either type of partition with no acrobatics needed!

---

### Post by merlinus on 2009-06-24
Only windows needs to live on a primary partition.

You have several choices.  You can leave the ntfs partition alone, format it as ext3 (or ext4, if you like to take chances), and use it for data.

You can use it as a /home partition, moving your existing /home directory.  Details here on how to do this:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Finally, you might shrink /swap (sda5) to 1.5 G and give the leftover space to / (sda6).

---

### Post by MartinEve on 2009-06-24
Hi,

Thanks for all the incredibly speedy replies - much appreciated.

I am going to do this (can you advise if this is a good plan?):

Delete the NTFS partition.
Shrink the swap to 2gb
Grow my ext3 partition to the remaining space

(I already have /home mounted to a different RAID device)

Thanks again,

Martin

---

### Post by mk1w86 on 2009-06-24
I don't know if you know this but you will have to grow the extended partition before growing the logical ext3 partition.

---

### Post by MartinEve on 2009-06-24
> **mk1w86 said:**
> I don't know if you know this but you will have to grow the extended partition before growing the logical ext3 partition.

Which, presumably, I can do from the GParted Live CD?

---

### Post by merlinus on 2009-06-24
I fail to understand why martin will need to grow his extended partition, if what he is doing is first shrinking /swap and then growing / to encompass the freed up space, since both are logical partitions.

But yes, if he is wanting to use the existing ntfs partition space for adding to /.  But then he will first have to delete /swap entirely, since partitions can be grown only into adjacent space.

---

### Post by MartinEve on 2009-06-24
> **merlinus said:**
> I fail to understand why martin will need to grow his extended partition, if what he is doing is first shrinking /swap and then growing / to encompass the freed up space, since both are logical partitions.

But yes, if he is wanting to use the existing ntfs partition space for adding to /.  But then he will first have to delete /swap entirely, since partitions can be grown only into adjacent space.

merlinus,

Thanks for the reply.

Have I understood correctly that the process I should follow is:

1.) delete ntfs
2.) delete swap
3.) grow extended partition
4.) grow / partition
5.) recreate smaller swap

Thanks again,

Martin

---

### Post by mk1w86 on 2009-06-24
> Which, presumably, I can do from the GParted Live CD?

Yes

> But yes, if he is wanting to use the existing ntfs partition space for adding to /. But then he will first have to delete /swap entirely, since partitions can be grown only into adjacent space.

I assumed that is what MartinEve was planning to do and it should be OK to delete and recreate a swap partition because it contains no important data.

---

### Post by merlinus on 2009-06-24
It depends upon what you are wanting to do with your current ntfs partition.  If you want to add the space to /, then yes, you will have to delete it and /swap, then grow the extended partition, add its space to /, and then recreate /swap.

But / is certainly big enough even as it stands, unless you will be adding loads more apps.
So the easiest solution, imffho, is to format the ntfs partition as ext 3 and mount it as /data.

If you do this, it will be very easy to shrink /swap and add that space to /, since they are continguous.

---

### Post by MartinEve on 2009-06-24
Perhaps I will just leave it for now then; just seemed uneconomical to have all that unavailable space.

I wouldn't actually use it for storing data because it isn't mirrored in any way.

Thanks again,

Martin

---

