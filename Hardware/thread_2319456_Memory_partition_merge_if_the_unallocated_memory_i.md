---
title: "Memory partition merge if the unallocated memory is not in order"
date: 2016-04-04
forum: Hardware
---

### Post by adarsh5 on 2016-04-04
[COLOR=#111111][FONT=Ubuntu]I have ubuntu 14.04 running on my laptop along side windows 10. I have been getting the error in ubuntu for insufficient memory space. So I am planning to merge one other partition that I created using windows disk management to ubuntu. The question has been answered in many other tags but I did not find any of them helpful for my case. Could you please let me know if I can merge the first parition that is dev/sda1 with the last partition which is unallocated which is of 268GB. Attached is the screenshot of the GParted too[/FONT][/COLOR][ATTACH=CONFIG]268162[/ATTACH]

---

### Post by ajgreeny on 2016-04-04
No, it is not going to be possible to do what you want as the two partitions are one at each end of the disk, separated by all the other partitions, including your Windows partitions which do not take kindly to being shifted on disk.

What you could do is create a new ext4 partition in the final unallocated space and either make it into a separate /data or separate /home partition.

What worries me is your comment that you have Ubuntu alongside Windows 10, but your Windows partitions sda3 and sda4 are both logical partitions.  Windows will not normally boot from a logical partition so I wonder if you can confirm whether or not Windows is still bootable.

Let's go one move at a time; give us an answer to my query and we can try to decide where we go from here.

---

### Post by adarsh5 on 2016-04-04
Thank you for the response.
Yes, I am able to boot my windows platform 10 in a normal way.

---

### Post by X-RED_Tech on 2016-04-04
Short answer is no. You can only extend a given partition to contiguous unallocated space (unallocated space is NOT a partition).
Long answer: You need to swapoff, delete swap partition (redo it again later), move sda4 to the right all the way, move sda3 to the right (left of sda4). At this point you can extend sda1 into the unallocated space eventually leaving the necessary space (~2GB) for the new swap partition.

Needless to say data loss can happen (it usually doesn't but it's always a risky procedure).

---

### Post by ajgreeny on 2016-04-04
Sorry about my mistake in post #2.

Having looked again at the screenshot I see that the only logical partition is actually the swap partition not all the others on disk, so your Windows partitions are not logical as I first thought but primary.

My other comments about either merging the two end of disk partitions or moving all the rest still stand.  I did not even mention the possibility of moving all tyhe partitions you have as to the best of my knowledge moving a Windows partition, as mentioned before, is extremely problematical.

For a separate /home partition see [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving), though a simple search using a custom search engine such as [www.googlubuntu.com](www.googlubuntu.com) or my own [https://cse.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://cse.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao) will find many other links for you.  use search term "separate home partition after installation".

---

### Post by X-RED_Tech on 2016-04-04
And my mistake for not noticing sda3 as the Wisndows system partition. So no, do not move that one otherwise your Windows won't boot.

---

