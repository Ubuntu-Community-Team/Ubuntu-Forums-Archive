---
title: "SMR harddisks, ext4, gnome-disks vs. gparted and write performance mystery"
date: 2024-01-01
forum: Hardware
---

### Post by frankvw on 2024-01-01
Several years ago I bought a Seagate 8TB Archive harddisk which is an SMR (shingled magnetic recording) model. I use this disk as an archive (occasional sequential writes, otherwise just reads) so the performance issues with random writes and read-modify-write operations that SMR is justifiably notorious for do not apply, and I've been quite happy with this disk. It works well for what I need it for.

However, it came out of the box with NTFS and I never changed that, which over time became more of a pain (especially after power failures when the dirty NTFS failed to mount) so yesterday I decided to bite the bullet and replace NTFS with ext4. I first went the standard route: crank up the standard Ubuntu disk management utility from the menu (which is gnome-disks), delete the NTFS partion, create the ext4 partition in its place, and job done.

Well, yes, except that write throughput to the disk had dropped to well below 15MB/s which is terrible even for SMR disks. Mind you, that's with sequential writes on an empty disk! Even with NTFS I got three times that. Initially I suspected that ext4lazyinit might be the culprit, but that turned out not to be the case at all.

I then found [this thread]("https://ubuntuforums.org/archive/index.php/t-2370055.html") and as per the instructions there I used gparted to delete the ext4 partition, create a new GPT partition table followed by a new ext4 partition. And now write throughput to the SMR harddisk lies close to 100MB/s (sustained, not bursts through the HD's built-in cache!) which is considerably higher what I got on the NTFS partition on that same disk.

So I have no problem and I'm happy that it works so well now, but I can't help wondering what on Earth is going on here? What could explain this behavior? What is the difference between gnome-disks and gparted and how does that relate to sequential write throughput on an SMR disk? Is [this paper]("https://www.usenix.org/system/files/login/articles/login_summer17_03_aghayev.pdf") on ext4lazyinit and SMR relevant and if so, what does that have to do with the utility used to create the partition?

Ideas, anyone?

// FvW

---

### Post by TheFu on 2024-01-01
Was sector alignment an issue?  At this point, I don't trust gnome-disks to show correct information, much less handle writing to a disk in the most desirable way.

---

### Post by frankvw on 2024-01-01
> **TheFu said:**
> Was sector alignment an issue?

I have no idea. How do I determine that?

> **TheFu said:**
> At this point, I don't trust gnome-disks to show correct information, much less handle writing to a disk in the most desirable way.

Well, it created a partition that the OS happily mounted. So with my "simple user" hat on I struggle to understand how gnome-disks output would affect write performance... ](*,)

// FvW

---

### Post by TheFu on 2024-01-01
> **frankvw said:**
> I have no idea. How do I determine that?
I'd look for an error in the fdisk output that says something like this:

```
Device          Start        End    Sectors  Size Type
/dev/sdc1          34     262177     262144  128M Microsoft reserved
/dev/sdc2      262178   20739914   20477737  9.8G Microsoft basic data
/dev/sdc3    20739915 3907024064 3886284150  1.8T Microsoft basic data
/dev/sdc4  3907024896 3907026943       2048    1M Microsoft basic data

[B]Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
[/B]
```
Sector size matters, so if it were me, I'd google a bit, learn about sector size and why alignment is so very important, if I had the problem.  The output shown above, is from a drive that I partitioned BEFORE I had any 4Kb disks and sector alignment was more important.   Plus, I was simply ignorant.  That drive was for backups and already very slow - connected over USB, so trying to make it faster wasn't high on my list.

The manual, easy-way, to ensure partitions are aligned is to always align them on 1MB boundaries.  Just ensure the first partition doesn't start before the 1st MB and all the others should be aligned fine if your units for each are MB, not anything else.  There's lots of good articles about this - google finds them.

> **frankvw said:**
> 
Well, it created a partition that the OS happily mounted. So with my "simple user" hat on I struggle to understand how gnome-disks output would affect write performance... 

Mounting isn't a high bar for high performance. As you've seen, bad performance, average performance or even great performance can be achieved on the same physical disk, if only it is setup correctly.  It is our choice whether we want it enough to do a little research.

Sector alignment is one of the easier ways, but not using overloaded buses or slower connections are the next.  There are lots of articles that say performance can be degraded 20+% by having misaligned HDD sectors.  Catch it during setup and you can avoid that negative performance aspect.

With some file systems, we can tune the way they are accessed.  NTFS is known to have poor defaults under Linux.  Someday, that might change. We can hope.  I'm a few years behind on NTFS (I'm on 20.04 still), so perhaps it has been addressed. IDK. But the issue was known for over a decade and nothing was done to address it, so I won't be holding my breath.  Ext4 defaults aren't bad and very little is gained by any mount option tuning, though people do set noatime.  I do it too, but don't think of it as a performance choice.  Most of the options I use for ext4 have to do with security, so those aren't related to this at all.

We can also tune how the OS accesses storage, just a bit, using **hdparm**.  This isn't usually important until RAID is involved. Getting the chunk size, sector sizes, and cache sizes all setup for performance isn't a science.  Add in that different workflows can drastically change which settings help the most, so it is possible to degrade performance for some workflows too.

It is up to you do decide if you want to do the research to learn these things. Now you know they exist and can choose to do some reading to make an informed decision.  Heck, you could ask some AI tools for their answer. Take it with a caution. Always validate what any AI says using reputable sources.

For example, here's the question I asked:
[https://iask.ai/?mode=question&options[detail_level]=detailed&q=What+steps+can+I+take+to+get+the+greatest+performance+from+a+HDD+that+has+GPT+partitions+and+EXT4+as+the+file+system+on+a+Linux+computer.++Consider+sector+alignment+hdparm+settings+and+mount+options.](https://iask.ai/?mode=question&options[detail_level]=detailed&q=What+steps+can+I+take+to+get+the+greatest+performance+from+a+HDD+that+has+GPT+partitions+and+EXT4+as+the+file+system+on+a+Linux+computer.++Consider+sector+alignment+hdparm+settings+and+mount+options.)

You may note that gnome-disks isn't mentioned.  I wonder why not?

---

### Post by frankvw on 2024-01-02
Thank you! This is definitely one of the more useful and informative answers I've had on a forum in quite a while.

I'm going to look into all this. Looks like something I need to know about.

Tnx!

---

