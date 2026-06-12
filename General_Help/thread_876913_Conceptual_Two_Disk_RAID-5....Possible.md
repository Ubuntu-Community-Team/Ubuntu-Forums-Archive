---
title: "Conceptual Two Disk RAID-5....Possible?"
date: 2008-08-01
forum: General Help
---

### Post by hodriver83 on 2008-08-01
Friday, August 1, 2008

Ubuntu Forum Members:

Hi all!  I've been wondering if this idea of mine will work or if it's even remotely possible.  I started thinking about it and today decided to ask some pros what parts of this, if any, are possible to implement.  Below is a link to a diagram which helps to illustrate what it is I'm trying to do.  The best way to explain it in words is to say that I'm trying to achieve striped-array performance as well as mirrored-array redundancy using only two disks; in other words, a 2 disk RAID-5.  Please click the link below to see the diagram (I've also included the diagram as an attachment to this post for those of you who would rather not click on random links.).

[http://communityelite.serveftp.net:8769/Two_Disk__RAID-5.png](http://communityelite.serveftp.net:8769/Two_Disk__RAID-5.png)

What do you guys think?  Is it possible?  Please let me know.  Any and all input and/or criticism is welcome!

Thanks,
Ed

---

### Post by Krupski on 2008-08-01
> **hodriver83 said:**
> Friday, August 1, 2008

Ubuntu Forum Members:

Hi all!  I've been wondering if this idea of mine will work or if it's even remotely possible.  I started thinking about it and today decided to ask some pros what parts of this, if any, are possible to implement.  Below is a link to a diagram which helps to illustrate what it is I'm trying to do.  The best way to explain it in words is to say that I'm trying to achieve striped-array performance as well as mirrored-array redundancy using only two disks; in other words, a 2 disk RAID-5.  Please click the link below to see the diagram (I've also included the diagram as an attachment to this post for those of you who would rather not click on random links.).

[http://communityelite.serveftp.net:8769/Two_Disk__RAID-5.png](http://communityelite.serveftp.net:8769/Two_Disk__RAID-5.png)

What do you guys think?  Is it possible?  Please let me know.  Any and all input and/or criticism is welcome!

Thanks,
Ed

Wow... what an interesting idea. Your sketch (image) looks more like a RAID 0-1 (stripe + mirror) to me than RAID-5.

The only thing is... say you used two 1TB drives. Each drive would be split 500 gb / 500 gb and mirrored.

Therefore, you would end up with a stripe drive of 1 TB (spanning 2 drives) and a mirror of those drives (spanning two drives).

Now, I'm trying to wrap my mind around the question... would it be faster than a plain RAID-1 mirror setup?

You WOULD have two 500 gb drives in a striped configuration... so theoretically it should be faster than one drive. You WOULD have mirror redundancy... since each drive is mirrored on the other.

I just wish I had a non-committed computer that I could test this on!

Interesting idea... VERY interesting.

-- Roger

---

### Post by jimv on 2008-08-01
RAID 5 is basically mirroring and striping.

---

### Post by hodriver83 on 2008-08-01
First, thanks for taking the time to look over this and give me some feedback.  Yes, it does function very much like a 0+1, but it only employs two disks.  I'm certain that the idea works in theory.  That's why I'm referring to it as a conceptual 2 disk RAID-5.  However, finding a controller or software solution to implement it might be a little more tricky.  Especially considering that most two disk solutions have the option of speed or redundancy, but not both.  

This is essentially the same as a three disk RAID-5; only instead of the redundant data being spread over multiple disks, each disk contains all data necessary to continue functioning.  Hypothetically, you could use this configuration with many more disks, but you would gain only speed considering that each disk contains a full system image.  The advantage, however, would be in the ability to survive multiple disk failures.  Each disk failure would degrade the performance, but you would retain 100% data integrity so long as you maintained one functional disk at all times.  

If you can come up with a method for testing this, I can come up with the hardware.  I'd be happy to try it out and document everything.  I've even got a camcorder I could use to catch some of it.

---

### Post by c2olen on 2008-08-01
> **jimv said:**
> RAID 5 is basically mirroring and striping.

What gave you that idea?

Read [this]("http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks") for more information on RAID5. You can consider RAID10 to be mirroring and striping though.

In your two-disk raid setup, you will get your arms in the disk do the shuffle, because a write operation can get striped, and will attempt to write in the corresponding partitions on your disk, and simultaneously try to mirror this to the other partitions. The disks will be scratching in your machine.... 
If you consider plain RAID1 (mirror) of the entire disks, you will get better performance than your suggestion. RAID1 read activity will normally try to read from both available disks in the mirrorset, and will give you better performance than single disk setups.

Just for testing purposes, you could setup a Virtual Machine with some VDI or VMDK disk images. Try to configure those disks to match your suggestion. You could run some tests, and then setup those VM disk files to a normal RAID1 set and rerun the tests. See what works better.
I haven't got time to do it now, but i'll give it a try later this weekend, unless someone beats me to it.

---

### Post by c2olen on 2008-08-01
> **jimv said:**
> That's why I'm referring to it as a conceptual 2 disk RAID-5. 

RAID5 indicates a paritydisk, and your setup hasn't got a  paritydisk(partition) so RAID5 really doesn't fit in this concept.

Nevertheless the concept deserves some discussion.

---

### Post by hodriver83 on 2008-08-01
Originally Posted by c2olen

RAID5 indicates a paritydisk, and your setup hasn't got a paritydisk(partition) so RAID5 really doesn't fit in this concept.

______________________________________________________________________________________________


I'm using RAID-5 to describe the qualities of the array, not the layout, configuration, or anything.  I suppose it would be better named "two disk RAID w/redundancy and striping", but that's just too damn long to type or say.  Let's find a name for it.  Also, the goal here is not to increase write performance one bit.  The primary goal is to increase read performance.  In the case of a workstation/desktop, games would load faster.  In the case of a server, files would be more quickly delivered.  I haven't tried it in practice yet, and to be honest I've got enough drives to setup a proper RAID-5 array as it is, but I really just wanted to try and squeeze the absolute most (in features) out of two cheap drives.  You know, like a poor man's RAID; just to see if it was possible.

Thanks for the input.  I didn't expect my post to get much attention.  I really like digging into things like this.

---

### Post by c2olen on 2008-08-01
Ok, I can go with you on this for a great part, but i really doubt you will get improved read performance.
As I stated earlies, under normal circumstances a read action on a mirrorset would try to read from as many spindels as possible. Since you are referring to softraid, you should be able to disable this read behaviour. But assuming this behaviour is true for your setup, this would mean a read from the stripe also means a read from the mirrorset, therefore the read should occur on all 4 partitions. Since the arms cannot be positioned at two places at the same time one (actually on both disks) of the read attempts have to the other read on the same disk to complete, therefore mitigating all read performance gain you'd expect.
Unless you can turn the read-from-all-mirror-members feature off, or if it isn't configured like that at all, this would actually reduce performance in comparison to a normal full-disk mirror-set.

nice discussion...

---

### Post by hodriver83 on 2008-08-01
I don't see why at all it would read from all four data groups at the same time.  While it must write to four groups (two per disk) at the same time to maintain redundancy, it only needs to read from one contiguous data set in order to read effectively.  

If the array was configured to read one half of the data from one drive and the other half from the other drive, then it would perform something like a striped pair; half and half.  However, you've brought up an interesting point I didn't consider.  What if the drives read from all four sections simultaneously by default.  While that would seriously hinder performance, effectively halving your read-rate, the optimal outcome would result in a doubling of the read-rate.  That being considered, if read performance cannot be increased, then the purpose of the project has been negated and one would be much better off going with a RAID-1 configuration.

---

### Post by jimv on 2008-08-01
> **c2olen said:**
> What gave you that idea?

I was thinking of it in terms of striping with redundancy.

---

### Post by Krupski on 2008-08-15
> **c2olen said:**
> In your two-disk raid setup, you will get your arms in the disk do the shuffle, because a write operation can get striped, and will attempt to write in the corresponding partitions on your disk, and simultaneously try to mirror this to the other partitions. The disks will be scratching in your machine....

The question is... how often is the mirror updated?

If disk writes and mirror updates are cached (as I imagine they should be), then the disk heads may not actually be thrashing around as much as you think.

Disk READS do not involve mirror updates (unless some sort of "last access time stamp" thing is recorded)... so maybe the striped part of this setup would yield faster data transfer on reads.

I imagine that this 2 disk "Raid 0-1" setup would have varying degrees of performance, depending on the drives (fast interface? native command queuing? cache size of the drives? intelligent seeking?)

The newest SATA drives would probably perform the best and old parallel IDE drives might actually get bogged down... only way to know for sure is to actually test it.

As I said before, too bad I don't have any uncommitted hardware to play with... this is an INTERESTING idea!

-- Roger

---

### Post by psusi on 2008-08-15
> **jimv said:**
> RAID 5 is basically mirroring and striping.

No, it is not.  Striping with mirroring is raid 0+1, aka 1+0 aka raid10.  Raid 5 involves striping with parity that can be used to reconstruct the missing data block if only one data block is missing from the stripe.

To answer the OP: the short answer is no, it is not possible.  The long answer is that you end up with parity blocks that contain the exact same data as the data blocks, which is really just a raid1.

---

### Post by Krupski on 2008-08-19
> **hodriver83 said:**
> 
What do you guys think?  Is it possible?  Please let me know.  Any and all input and/or criticism is welcome!

Thanks,
Ed

I had another idea (or question?)... to create the array you mentioned, I assume first one would create 2 partitions on each drive, like this:

/dev/sda1, /dev/sda2
/dev/sdb1, /dev/sdb2

Now, to create a RAID 10 array with MDADM, one would use the -C (create) command, -n4 (number of drives=4) and the list of partitions.

BUT! How would MDADM know which to use? Would it make a mirror on one physical drive and then stripe the two drives (i.e. useless)?

Or, would I have to "fake it" by creating one mirror drive called /dev/md0, a second mirror called /dev/md1 and then a striped mirror called /dev/md3 consisting of /md0 and /md1?

Oh boy...my head hurts now!

---

