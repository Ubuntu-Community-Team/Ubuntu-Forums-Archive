---
title: "defrag"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by mr.farenheit on 2007-03-12
does ubuntu have a similar feature as to window's defrag and disk clean up features and if so where do i find them?

---

### Post by amd-64 on 2007-03-12
The short answer is no, you will not need to defrag.

If you want more information, the default ubuntu installation is set to check the filesystem (ext3) every 30 mounts (reboots) or 30 days. 

The settings are controlled by tune2fs. I encourage you to read the help ```
 man tune2fs 
``` Please be very careful it you plan to apply any changes to the settings.

---

### Post by Mr. C. on 2007-03-12
This isn't quite correct, but as a short answer is close enough.  Some fragmentation can occur, but it is handled much differently in ext2 than in NTFS, and is far more efficient.

The file system check ensures file system integrity, and does nothing for the marginal fragmentation that can occur.  The only way to defragment an ext2 disk is to do a dump/restore.

The tune2fs does not defragment the file system.

MrC

---

### Post by amd-64 on 2007-03-12
Thanks for the correction

---

### Post by FUbuf on 2007-09-10
Is there any good online defragger for Ubuntu, or even Offline?

I personally think and know that defragging is needed sometimes or even frequently. So I would like to do it with my Ubuntu. Or is rewriting data to partition only solution? As far as I know it might cause fragmentation on dump/restore routine itself. Like directory fragmentation if there are large number of files in one directory.

I also thought at one point that defrag isnt needed, but I think very differently now.

---

### Post by Linicks on 2007-09-10
You don't need to defrag a Linux filesystem, so you can safely forget all about it :)

Nick

---

### Post by Old *ix Geek on 2007-09-10
> I personally think and know that defragging is needed sometimes or even frequently...I also thought at one point that defrag isnt needed, but I think very differently now.You really need to stop thinking like a windoze user!  In 20+ years of using *nix I've never "needed" to defrag a drive.  In fact, I'd never even heard that term until [unfortunately] crossing over to the dark side--and, yes, I laughed at the concept.  Imagine that!  A file system that is so inherently screwed up that you actually have to put pieces of files back together. :lolflag:

---

### Post by Soybean on 2007-09-10
> **FUbuf said:**
> Is there any good online defragger for Ubuntu, or even Offline?

The default filesystem in Ubuntu is ext3, and there is no defragger for ext3 filesystems. If you set up your Ubuntu install with a different filesystem, there may be a defrag tool available. For example, I believe that XFS and ext2 both have defrag tools.

The thing is, defrag tools (even offline ones) don't work very well with partitions that are very full. And ext3 partitions don't get fragmented unless they are very full. So since the only time you'd need it is when it wouldn't work anyway... nobody has taken the time to make one. ;)

---

### Post by philinux on 2007-09-10
Ok hear you all load and clear on defrag what a super system.

What about disk clean up then I'm sure some uninstalls have left empty folders etc about?

---

### Post by jongkind on 2007-09-10
> **Soybean said:**
> The default filesystem in Ubuntu is ext3, and there is no defragger for ext3 filesystems. 

Well, there is a defragger::
[http://ubuntuforums.org/showthread.php?t=169551]("http://ubuntuforums.org/showthread.php?t=169551")

And here is the reason why I use this tool:
[http://ubuntuforums.org/showthread.php?t=203842]("http://ubuntuforums.org/showthread.php?t=203842")

---

### Post by Soybean on 2007-09-10
> **jongkind said:**
> Well, there is a defragger::
[http://ubuntuforums.org/showthread.php?t=169551]("http://ubuntuforums.org/showthread.php?t=169551")
Huh. Well, there you go. #-o

Do notice that even the guy who made it says that most people don't need a defragmenter for Linux, and those who do don't need it often.

Personally, I figure that the guys who developed ext3 probably know a lot more about it than I do, and if they didn't think they needed a defgramenter, then I'm probably ok without one too. :) But sorry for claiming it didn't exist -- I was just repeating what Wikipedia told me.

---

### Post by FUbuf on 2007-09-15
> **Soybean said:**
> Personally, I figure that the guys who developed ext3 probably know a lot more about it than I do, and if they didn't think they needed a defgramenter, then I'm probably ok without one too. :) But sorry for claiming it didn't exist -- I was just repeating what Wikipedia told me.

To clear some points.

First, how ever I read ext2/ext3 documentation I don't find any reason why it would totally prevent fragmentation. Fragmentation is still possible and in some cases very probable. When I were using IBM system. (IBM-36) It had a file system which totally prevented fragmentation. And it got good and very bad sides. If file did run out from preallocated and reserved space then system did crash.

I know a ton of computer users who never run defrag with XP / NTFS systems and they also work well. They just don't notice long time performance degrade.

I started to look for defrag tool because my file server is having performance problems.

There is one large main file which contains a lot of data. It's size is now about 25 gigabytes. Also during the process when that file has been growing there has been a lot of small constantly changing files. 

If small files are scattered around as they are. It means that large file has to encounter those files when growing. Meaning that fragmentation occurs at those points.

Another good point which I keep very important is that ext3 doesn't use pre allocation at all nor support it. But NTFS does support it. Meaning that if it is possible to accommodate enough large space for large file it will use that slot. Ext3 doesn't do that. And it's a fact.

Pre allocation helps when some large file is copied. But even it wouldn't prevent fragmentation in my case. Because file is constantly growing for several years. 

I heard several guys saying that ext2/3 doesn't need defrag. But they didn't explain how file system prevents fragmentation. And they couldn't because it doesn't. [Old *ix Geek, Linicks]

Soybean was right, there are situations when files can get fragmented. 

Let's take very simple and straight forward sample.

1) Allocate 40% disk space using 4 kilobyte files. To prevent fragmentation when those files are growing they're allocated sparsely. Then add one file using up 50% of disk space. After this process we'll got 10% of free space. 

We can still continue this sample. Now when drive starts getting full. We'll delete those small files. At this point we got serious free space fragmentation. Then we add 40% (total disk space) to that large file. Now it will be even more fragmented. 

That's very easy for everyone to understand because it's simple sample. Then it's yet another thing what kind of effect it got in real world.

2) It would be nice to time reading time for that file. And then erase all files and do same test but place that large file first and then small files. Reading time should be exactly the same if files weren't fragmented last time. But will it be? ;)

If ext3 would support pre allocation it would be easy to rewrite files to partition and get those defragmented. Of course it wouldn't help in this sample scenario because this is too extreme. But for general 1-2 gig files and smaller number of small files it should do it's job pretty well. Then it's only the question how many programs do pre state file size which is going to be written to disk? I guess it's next to nil. 

Proper defragger should result about same disk data layout with sample two when starting with sample one. 

But I have to admit that with NTFS I have encountered most horrible  fragmentation every.

I'll create empty 2 gigabyte file with NTFS compression enabled. Then I start filling that file in random order with 4 kbytes random data. Guess what? Result is that almost every cluster in that file is non-contiguous. One test file had after testing 483k non contiguous fragments. Think about that. ;) Reason why I did this test? I were using ntfs compression for emule temp directory. And I started to wonder how much my drive fragmented. Then I found out the reason and made this ultimate fragmentation test.

With these samples when using large number of small files. On-line defrag would be nice. Moving small files when large grows wouldn't be a problem. But in real world we might have only many large files. Then on-line defragging would be way too slow.

Finally. Because fragmentation clearly can occure. It would be good to do defrag. In longer time perioid fragmentation without defrag usually simply gets worse and worse, especially because free space fragmentation. Running defrag 4 times / year wouldn't be too bad, and it would take care of system file etc fragmentation, so it won't get extremely bad.

One reference from real world:
[http://www.webservertalk.com/archive202-2005-5-1037740.html](http://www.webservertalk.com/archive202-2005-5-1037740.html)

If I got something totally wrong, I'm very happy to hear what I got wrong and why. But I hate discussions without any thoughs or facts.

---

### Post by lisati on 2007-09-15
Reading FUbug's comments about IBM System 36 reminded me of the days I used MVS  - also an IBM system. It preallocated space for files, with an option for specifying how much to allow for allocating extra space each time it was extended. Once certain limits were reached, programs trying to append to the file would crash, often with memory dumps that were largely incomprehensible to the average user.

---

### Post by psusi on 2007-09-15
Actually the 2.6 kernel does use preallocation.  Of course, it isn't perfect because it doesn't really know how large the file is going to get, but it does reserve space for it to grow without being fragmented, and other files are placed randomly in free space rather than right after the first file.  

Windows does not do this, which is what leads to 10 meg files being scattered around in 5000 different fragments, on a large disk with plenty of free space.  

You can install the defrag package if you wish, but you won't likely see any change.  The package has not really been maintained for at least 8-10 years because nobody ever needs it.

---

### Post by FUbuf on 2007-09-16
> **psusi said:**
> Actually the 2.6 kernel does use preallocation.  Of course, it isn't perfect because it doesn't really know how large the file is going to get, but it does reserve space for it to grow without being fragmented, and other files are placed randomly in free space rather than right after the first file.

Yep. Actually using random placement makes my example just worse. Large number of small files fragment free space very badly. When writing any larger file it's going to be sure that it is going to be fragmented.

- is free space S is some small file.

-S--S----S-SS-S--S-SSS---S-S--S--

And now to place there let's say 8 clusters large file. In best case it's going to be in three fragments. If system would know in advance it's going to be 8 clusters big. But because it doesn't know that. It might be as well in 4-5 fragments easily.

And I know 2.6. reserves 8 block batches. But that reservation isn't maintained when files are closed. And with large files it would be very important to reserve whole file sized space at once. But with about 50% full disk it is improbable that there is lets say 2 gigabyte contiguous free space due random file placement.

Especially databases and logs are continuously growing files. Which are fragmented for sure using this approach to fragmentation problem. It's lot better than first free cluster allocation but doesn't solve fragmentation problem.

Thank you for your responses everyone. I wasn't aware of that 8 block batch allocation before I really studied this thing before writing here.

---

### Post by deserthowler on 2007-09-16
My rule of thumb is "If Debian doesn't have it, I probably don't need it."
I haven't heard anyone I know personally using slack or fedora talk about defragging either.

Of course, I'm not using Gigantic files.  If I ran a large scale server, I might consider something like that.  I'd be more concerned, though, about having a defrag program not included in my repositories bust something than about the inefficiency of a fragmented disk.

Earl

---

### Post by psusi on 2007-09-16
Of course large files are not going to be fully contiguous, but when you have a 1 gig file that is in 5 200 meg fragments, that's not a problem.  You only start to see performance loss when you have a 10 meg file in 200 fragments.  

And the defrag package is in the repositories and we inherited it from debian.

---

### Post by FUbuf on 2007-09-19
> **psusi said:**
> Of course large files are not going to be fully contiguous, but when you have a 1 gig file that is in 5 200 meg fragments, that's not a problem.  You only start to see performance loss when you have a 10 meg file in 200 fragments.

Exactly. That's true. I didn't say fragmentation would be instant problem. As I told my fragmentation problem was created due huge number of small files (over 200.000) in volume and a few very large databases in that same volume. And volume has gotten almost full a few times and when that happens we delete small files which have been merged to database.

But this causes not as extreme as my example, but in long run it causes very heavy fragmentation. Meaning a lot of small non-contiguous parts. Free space is always very heavily fragmented and when  databases grow they occupy that fragmented space.

That's why I would run 4 times a year that defragmentation process. Or preferably when small files have been deleted.

Even with my Windows system I run defrag a few times / year and it helps. But there is no point running it too often.

Just to tell for curiosity. Windows Vista doesn't try to consolidate larger than 64 megabyte blocks. So if you have 64 megabyte contiguous blocks in 700 megabyte file. Whole file wont be defragmented. Only those parts are defragmented which are in smaller fragments.

After running dump&restore you might already have some fragmentation. You should copy files using largest first order. And about to that system works fine without defrag. 

I have seen plenty of Win'9X systems that have been running with fat for 8 years without defrag. And I also truly believe that at least 90% of NTFS users never run defrag. Running it once / year still might improve performance.

---

### Post by Jaster on 2007-10-26
All filesystems can get fragmented, the only ones that don't are like the IBM one that crash if files get over their preallocated size ...

But, all sensible filesystems do not fragment (or do not fragment enough) if the drive is never very full that's the difference between ext2/3 and FAT and NTFS,  ext2/3 only fragments (except for very large files) if it gets very full, FAT fragments even if almost empty, NTFS seems to fragment (to a small degree) even if not full but if allowed to get full fragments to a huge degree  

Preallocation helps but can only prevent fragmentation if no file gets larger than the preallocated size, Linux does not have defrag tools simply because it is not normally a problem unless you are low on disk space, the usual solution to a full fragmented disk is backup the contents delete everything and restore what you actually need on the disk from the backup ... this will remove the fragmentation

---

### Post by deserthowler on 2007-10-26
> **psusi said:**
> And the defrag package is in the repositories and we inherited it from debian.

OOPS.:oops:  I looked and couldn't find one.  Well, I guess that's something to do if I ever start missing Windoze. :idea:

Earl

---

### Post by esaym on 2007-10-29
Yea this aint windows [http://www.lindsay.ath.cx/pics/fragged2.jpg](http://www.lindsay.ath.cx/pics/fragged2.jpg)

The only time you would ever notice a performance problem with ext would be from a giant heavily fragmented file with the disk almost full.  As far as non-continuous files, there really is no performance hit if a file is broken into 2 or 3 other parts.

---

### Post by FUbuf on 2007-10-31
> **esaym said:**
> Yea this aint windows [http://www.lindsay.ath.cx/pics/fragged2.jpg](http://www.lindsay.ath.cx/pics/fragged2.jpg)


Pretty nice screen shot... That's just like the server disk which I described. 

Actually after thinking for a while. I would say that coolest ever solution would be true on-line defragmentation feature in kernel which eliminates fragmentation during normal disk usage.

If we think large files, they're bit a problem. But if we use crumb approach then even largest files aren't a problem, because we only care about crumbs. As does Vista's defrag,

When ever system reads file which is heavily fragmented. It should simply look for place to drop that data. Because we have already used something like 70%-90% of (disk) time needed to defrag heavily fragmented file when we did read it. Now it's in cache so we can write it out in 30%-10% of time. And fragmentation has been eliminated in the process.

I know this has been a problem with systems before. But with multitasking, multi core and high i/o systems. It can flag data in cache during read to be defragmented and when ever there is suitable low i/o gap it should do it. Using access logs would help this process, but keeping logs would also take resources so I think it's not worth of keeping those logs. Just do defrag immediately and it's done.

For performance critical environments this could be disabled naturally. And also crumb size affects a lot with this kind of process. Vista uses 64 MiB crumb but that might be bit high for this process. Something like 256 KiB to 64 KiB would be rather nice. Users wouldn't notice anything. And naturally that process can be done in background with low priority and in smaller chunks. So if there is what so ever disk i/o it will be taken care first.

What do you guys think about this? I would say this approach would be coolest ever. At least me my self as old tech geek would love to hear something like this. It's smart and sexy. ;) 

And then I would also believe there is a system which doesn't need separate defrag routine.

---

### Post by Rinzwind on 2007-10-31
> **philinux said:**
> Ok hear you all load and clear on defrag what a super system.

What about disk clean up then I'm sure some uninstalls have left empty folders etc about?
I think people missed this question.

Linux uses libraries that are shared among all kinds of software.
Those 'libs' stay on your system if it's not known if they are no longer needed.

The package 'deborphan' scans for those and let's you delete them (with of without backup)

---

### Post by Jaster on 2007-11-01
"Actually after thinking for a while. I would say that coolest ever solution would be true on-line defragmentation feature in kernel which eliminates fragmentation during normal disk usage."

This is a solution looking for a problem - If your disk is getting fragmented you need more disk-space! If you need to defrag at all then in most cases it is because you let the disk get full, the solution is to free up some disk space, then defrag (but it's often quicker to move the contents to backup and restore which will often work better than many defrag tools). Unless you are using FAT then a filesystem with adequate free space will not fragment enough to make it worth defragging ...

Vista has an online defragger simply because people know "Windows need defragging to improve performance" ... this is simply not true anymore, unless you let the disk get full!

---

### Post by esaym on 2007-11-01
> **FUbuf said:**
> Pretty nice screen shot... That's just like the server disk which I described. 

Actually after thinking for a while. I would say that coolest ever solution would be true on-line defragmentation feature in kernel which eliminates fragmentation during normal disk usage.



The devs are hard at work trying to get that into ext4.  Not sure if it is going to happen though.

---

### Post by FUbuf on 2007-11-01
> **Jaster said:**
> If your disk is getting fragmented you need more disk-space! If you need to defrag at all then in most cases it is because you let the disk get full, the solution is to free up some disk space, then defrag (but it's often quicker to move the contents to backup and restore which will often work better than many defrag tools). 


I agree with you completely. If there is enough free space (excess) fragmentation can be avoided during allocation. 

But in normal operation (as far as I have seen it in last 10 yers) it usually go somewhat this way: Everything is fine, nobody cares... And suddenly ***t disk is almost or actually completely full (in worst case) let's clear up some space. And in that case fragmentation has already been building up for a while. 

How to get rid of that mess is the question. Often busy home / office users don't really want to waste time with backup / restore solution. In that case on-line defrag which I described would automatically take care of problem during normal disk usage.

I know it's stupid to let disk become full, but it just happens. And in case of non-professional and or non-enthusiastic administrators that's just the normal situation. 

It's like letting systems run with raid1 after one of dissk has failed several months a go. It's not smart, but it simply happens.

Real world example. You'll flag a lot of stuff to be downloaded using eMule. In configuration panel absolute maximum value for "stop when there is less free space than" is 4 gigabytes. Default value is something like 500 megs. I have 500 GB drive. if there is 4 gigabytes free it's less than 1%. And I'm sure that most of users doesn't set that value so high.

I know. I'm long term professional, but there are plenty of non-pro users out there.

---

### Post by jongkind on 2007-11-01
> **FUbuf said:**
> I agree with you completely. If there is enough free space (excess) fragmentation can be avoided during allocation. 


I partly agree. However [this happens]("http://ubuntuforums.org/showthread.php?t=203842") with 70 % free space of a 135 GB partition, so...

---

### Post by esaym on 2007-11-03
> **jongkind said:**
> I partly agree. However [this happens]("http://ubuntuforums.org/showthread.php?t=203842") with 70 % free space of a 135 GB partition, so...

> **esaym said:**
> As far as non-continuous files, there really is no performance hit if a file is broken into 2 or 3 other parts.

Non-continuous is not always a horrible thing.  Any file that is broken up into 2 or more sections is counted as non-continuous.  Most people that really dig into their file system find that the high non-continuous count is usually caused by some small config or log files which really don't hurt anything.

---

### Post by lyndaj70 on 2007-11-03
I've ran Windows and Linux side by side for years, and was paranoid about fragmented files as well....

But keeping an eye on my fragmentation level when fsck ran automatically after so many boots, I noticed that my overall fragmentation level on a single partition with a parition for swap was always LESS than 5%.  This was on a system that was heavily used.

On a Windows PC even moderately used, the percentage of fragmentation would just keep climbing until you defragged it.  In Linux if it was 5% one time the next time it MIGHT be 2%.....

I don't know how it works, just that it does....

As far as removing temp files.. there is a program called "Kleandisk" I have used in the past....

~L

---

### Post by tubasoldier on 2007-11-03
I think mine is at 11% non-contiguous or something close to that. I also have a lot of large files as well as a lot of smaller pictures. Put large and small together and see what happens. But thats why the filesystem is journalised  But to be paranoid about fragmentation just goes to show how easily people can be trained to believe that something is a problem. Viruses are an issue with windows too, as well as spyware. Its amazing how many posts there are on this forum about all these issues. Basically if it isn't recommended it's not needed. Notice firewalls are recommended.

---

### Post by atlfalcons866 on 2007-11-04
a journal dosent have anything to do with fragmentation. It just helps make the file system consistant after a hard poweroff. NTFS is journaled and that just fragments everytime a new file is added.

---

### Post by Erunno on 2007-11-09
Ah, the myth about Linux not having fragmentation issues surfaces once more :) I'm always amused by the notion that if Linux does not have a feature (in this case: online defragmentation) then it doesn't need it. Here's a [link]("https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf") to a paper describing current problems with fragmentation and what measures ext4 will probably implement to prevent to said fragmentation (including online defragmentation).

---

### Post by psusi on 2007-11-09
The method described there is essentially a slightly more refined version of jdong's python script defragmenter:  copy fragmented files to another location where they can be contiguous.  The difference is that with the python script, after defragmenting the file has a new inode number, but the way that paper describes, it won't.  

Personally I see no reason for online defragmenting when an offline defrag is faster and more efficient.

---

### Post by Ux64 on 2007-11-12
> **Erunno said:**
> Here's a [link]("https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf") to a paper describing current problems with fragmentation and what measures ext4 will probably implement to prevent to said fragmentation (including online defragmentation).

Thank you. I'll take a good look. And then I'll tell what I think about it.

[quote=psusi]Personally I see no reason for online defragmenting when an offline defrag is faster and more efficient.[/QUOTE]

In some cases online defrag can be set to occure during low load times. Although service can't be totally down.

I have seen so many different scenarios about these things. Any my opinion is that good defrag is needed at some point. Not too often. Maybe a few times per year. New block (extents) allocation based solution can't fix the problem if situation is bad. But I'll tell more after reading that paper and thinking a while.

---

### Post by atlfalcons866 on 2007-11-13
Cluster based allocation is in windows. Block allocation is unix and linux

---

### Post by pveith on 2007-11-13
Found this one on Drefagmentation in Windows and Linux. I think this could help to explain, why ext3 does not really have to be defragmented. ([http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting))

Other than that -if i recall correctly- fschk does output the count of non-cont. blocks on bootup (every 26-boots). And on all my systems the percentabe is very low and just get worse if the disk are very full...

---

### Post by Ux64 on 2007-11-13
> **pveith said:**
> Found this one on Drefagmentation in Windows and Linux. I think this could help to explain, why ext3 does not really have to be defragmented. ([http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting))


That article has been quoted in this thread several times. And it's partly true, not completely... 

ext3 is fragmentation resistant, but it doesn't prevent fragmentation.When ext3 gets fragmented (resistance fails for some reason, disk full, free space fragmentation etc.) it won't get fixed automatically. But I'll get back to this issue after analyzing that (excellent) ext4 article which was mentioned in this thread.

[https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf](https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf)

It's already in my slightly irregular bathroom reader library. ;) And that documentation looks really nice. I hate short messages telling something, without telling why or what are the technical real backgrounds for that case.

---

### Post by Ux64 on 2007-11-20
> **atlfalcons866 said:**
> Cluster based allocation is in windows. Block allocation is unix and linux

Thanks! You're right! I have been so long working with FAT and NTFS that it's hard to learn new terms. Like iNode.

Although ext4 seems to be quite much simpler than NTFS which is actually rather complex system.

I had a very pleasant and long reading break with that ext4 online defragmentation document. They addressed even one more problem that I wasn't caring too much. Which was relevant file fragmentation. Altough PC Tools compress took care of that problem in late 80's for DOS-systems. There was option to defrag disk using mode called directory with files. 

Most important thing from that document was conclusion section... I'll quote it here.
> 
**From: ext4 online defragmentation paper / Takashi Sato, NEC Software Tohoku, Ltd.**

Create the file by writing 32 1GB files sequentially.
Create the file by writing 32 1GB files from 32 threads concurrently. 
File read performance decreases about 15% for ext3.

Defragmentation for a single file can improve read performance by 25% on a fragmented 1GB file.

For relevant fragmentation, defragmentation resulted in 29% performance improvement for accessing all file in the Linux source tree.


I wouldn't call **up to 30% performance increase** meaningless. That's just why I would like to run defrag a few times per year. That's it.

- Thank you guys, it was nice to chat about this topic. But I think I have made my point and referenced it. So I'm not wasting more my and your time with this topic.

---

### Post by Ux64 on 2007-12-19
And what I just said earlier.

Today, important file server, ext3 ... Disk full... And after that situation, I would recommend running online defragmentation, if we would have one.

And even making some space, largest free block is less than 2 megabytes. So free space fragmentation is bad, causing also every larger new file written to disk to fragment.

... Nothing new ...

---

### Post by Ux64 on 2008-03-11
I also made few interesting tests. On NTFS volume. This is off topic, but gives you some clue how much pre-allocation can help.

```

w pre-allocation 8 fragmented files, 89 frags
 
w/o pre-allocation 200 fragmented files, 2152 frags

Total file count 1726, total size 800 MBytes.

```

---

### Post by articpenguin on 2008-03-13
preallocation helps with bittorrent. If you dont preallocate a 3.6GB ubuntu dvd image then you can guarantee that the file witll be fragmentented with more than 10k extents.

---

### Post by Ux64 on 2008-03-17
There is also another excellent point.

If fragmentation isn't a problem? Why they're still working to "fix" it?

<Flame mode> This sounds like typical engineering problem. Laugh! There is no problem, no what so ever. Ok, now we have new version. You should update. Err, why? Because ahem, it's just good idea to update. And they don't never ever admit that they were completely wrong. So... </Flame mode>

Read this. This explains why ext3 does need defragging.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

- Pre-allocation
- Delayed allocation
- Online defragmentation

Wait a sec... Why they're implementing those features, when there is no reason what so ever to do those?

Hmm... Read again what I said inside flame mode tags... ;)

---

### Post by Sef on 2008-03-17
Here is another article:

[Why Linux Doesn't Need Defragging]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

---

