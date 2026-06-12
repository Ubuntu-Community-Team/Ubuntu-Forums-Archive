---
title: "Changing Hard Drive improved performance."
date: 2022-06-02
forum: Hardware
---

### Post by rsteinmetz70112 on 2022-06-02
I've recently changed the hard drive in one of my Ubuntu 20.04 desktops. I was happily surprised at the result.

I did it because I could see that I would need some more space, although the drive was only about 70% used and I had some larger drives I removed for other computers to increase their storage. Using smartmon I didn't see any obvious problems. 

I cloned the drive using ddrescue then expanded the partitions and file systems using gparted. I then moved some of the files around. I had user home directories in two different partitions, I moved them all into one. 

The computer suddenly boots much faster, and all operations appear much quicker. The only obvious difference between the drives is that the 1GB Toshiba P300 7200 RPM SATA 6mb/sec has a larger 64mb cache. The original drive was a Seagate ST500DM002 7200 rpm SATA 6mb/sec drive with a 16mb cache.

Thought someone would be interested.

---

### Post by Autodave on 2022-06-02
More cache is always good!  Also possible that the old one was getting fragmented.  I just prefer to use an SSD for the boot and then use a good spinner for saving everything else.

---

### Post by rsteinmetz70112 on 2022-06-02
I've always ben told that Unix filesystems don't suffer from fragmentation.

---

### Post by TheFu on 2022-06-02
> **rsteinmetz70112 said:**
> I've always ben told that Unix filesystems don't suffer from fragmentation.

There are many caveats around that statement which get lost.

---

### Post by mIk3_08 on 2022-06-03
> **rsteinmetz70112 said:**
> I've recently changed the hard drive in one of my Ubuntu 20.04 desktops. I was happily surprised at the result.
I did it because I could see that I would need some more space, although the drive was only about 70% used and I had some larger drives I removed for other computers to increase their storage. Using smartmon I didn't see any obvious problems.
I cloned the drive using ddrescue then expanded the partitions and file systems using gparted. I then moved some of the files around. I had user home directories in two different partitions, I moved them all into one.
The computer suddenly boots much faster, and all operations appear much quicker. The only obvious difference between the drives is that the 1GB Toshiba P300 7200 RPM SATA 6mb/sec has a larger 64mb cache. The original drive was a Seagate ST500DM002 7200 rpm SATA 6mb/sec drive with a 16mb cache.
Thought someone would be interested.
It is true and strongly 101% if you change your hdd to sdd you will see the big difference in terms of speed. Before I used hdd on my laptop since my old hdd on my laptop has a lot of issues I did not hesitate to change it. But before I decided to change my storage, I've done a lot of study/research between the hdd and sdd storage because my budget is very tight so I come to be more careful of choosing storage. Which one is best fit to my needs. To make the story short, I'm Glad with the result of my study/research which I choose to have a sdd storage because I was so amaze in term of speed performance to my laptop. Since then I haven't regret of choosing ssd then that was 6 years ago and still now my sdd storage on my laptop is still in good condition. :-D Glad to say that I'm successful in my own little way of study and research about the storage. :-D Regards and Cheers.

---

### Post by Autodave on 2022-06-03
> **rsteinmetz70112 said:**
> I've always ben told that Unix filesystems don't suffer from fragmentation.

Linux is much better than Win at keeping fragmentation to a minimum, but it still happens.  And the fuller the drive, the more it happens.

---

### Post by rsteinmetz70112 on 2022-06-03
Since I cloned the drive using ddrescue I'd assume that any fragmentation would be copied exactly to the new drive. I did move my home directory from one partition to a new larger partition using rsync, so that would have been refreshed.

---

### Post by #&amp;thj^% on 2022-06-03
Linux&#8217;s ext2, ext3, and ext4 file systems &#8212; ext4 being the file system used by Ubuntu and most other current Linux distributions &#8212; allocates files in a more intelligent way.

 Instead of placing multiple files near each other on the hard disk, Linux file systems scatter different files all over the disk, leaving a large amount of free space between them. 
When a file is edited and needs to grow, there&#8217;s usually plenty of free space for the file to grow into. If fragmentation does occur, the file system will attempt to move the files around to reduce fragmentation in normal use, without the need for a defragmentation utility.
I had a friend that would move/copy large amounts of files/folders on a daily basis and after about 6 months worth of time his showed more fragmentation than I recall ever seeing in a Linux ext4 system.
Rare but it can happen.

---

