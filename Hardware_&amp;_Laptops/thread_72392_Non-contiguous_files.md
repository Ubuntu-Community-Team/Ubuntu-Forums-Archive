---
title: "Non-contiguous files?"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by NiceGuy on 2005-10-06
Hi, I booted up my machine the other day and much to my surprise, when I returned with a cup of coffee a couple of minutes later, it was still booting. It was complaining that the root file system was corrupt and was forcing a check. It finished and told me that I had 2.1% of non-contiguous files and then it continued to boot normally. When I next restarted It had no complaints so I ignored it (In the vague hope that it would go away) but alas I was wrong as it has just done it again.
After searching the forums I've come up with two possible answers, either a) my hard drive is on the way out (which would be a shame as its a Seagate and under a year old) or b) Ubuntu has become fragmented (which is odd because I've been told and have read numerous times that Linux just doesn't do this).
So I was wondering if any one could tell me which it is (HD failing or fragmentation) and how I can fix it.

---

### Post by DJ_Max on 2005-10-06
More than likely there's nothing wrong. If something was wrong it would have told you. Thats a routine check Linux does to keep it's speed.

When you save a file, the disk may scatter the data among noncontiguous clusters. So what it did was relocate broken or separated files from random, non-contiguous locations on a physical disk platter to contiguous locations to improve performance. It's similar to defragmenting, but not as extreme as what you've seen with Windows.

---

### Post by drummer on 2005-10-06
The check it was doing happens every 30 times you boot, it's just a routine check of the file system. 2.1% non-contiguous files is nothing, at least compared to windows.. last check on mine was 5.7% non-contiguous IIRC.
Last time I defragged a Windows machine (W2K) it looked from the graph pretty much like 100% non-contiguous (if not it must have been at LEAST 95%) :shock:

---

### Post by Declan on 2005-10-06
Ah, that's what it's about.
I've wondered about that.  I usually get 2.2%.
On my laptop, which gets many boots, the system runs this check every 30 mounts.  I suppose that's the default.

Declan

---

### Post by NiceGuy on 2005-10-06
I see, so does that mean that it is just checking the 'fragmentation' of the drive or actually defraging it? Obviously 2.1% isn't anything to worry about but how would I go about defraging my drive anyway, as I assume that this figure will slowly increase over time?
PS. thanks for all your replys, its put my mind to rest as a new hard drive would be an expense I could do without!

---

### Post by doclivingston on 2005-10-06
[QUOTE=NiceGuy]I see, so does that mean that it is just checking the 'fragmentation' of the drive or actually defraging it? Obviously 2.1% isn't anything to worry about but how would I go about defraging my drive anyway, as I assume that this figure will slowly increase over time?[/QUOTE]

There are some ext2/ext3 defragmenters around, but you can't use them on a mounted partition. I don't think I've seen a defragmenter for any of the other filesystems like XFS, Reiser, JFS etc.

Unix filesystems tend to be fairly fragmentation-resistant, and it only really become a problem if the are full (>95% usage). I've never seen any of mine go over about 3-4% fragmented, unless there were full.

---

### Post by az on 2005-10-06
[QUOTE=NiceGuy]Hi,  It was complaining that the root file system was corrupt and was forcing a check. It finished and told me that I had 2.1% of non-contiguous files and then it continued to boot normally. When I next restarted It had no complaints so I ignored it (In the vague hope that it would go away) but alas I was wrong as it has just done it again..[/QUOTE]

When you say that it did it again, do you mean it said the filesystem was corrupt, or that it just did the routine (oncer per thirty mounts) check?

---

### Post by NiceGuy on 2005-10-06
Urm... both I think, I just rebooted (again - ie. just now) and every thing seems normal so it may just be that '30 boots' thing but it did say the filesystem was corrupt (I'm fairly sure thats the word it used).

Why? *begins to worry again* :(

---

### Post by drummer on 2005-10-06
I think when it does the check the message goes something like "Checking filesystem on / for errors" or somesuch, so you may have read errors or corrupt in that.

---

### Post by dpj23 on 2007-11-23
Information on this subject:

1. Ubuntu checks the files every 39 times the drive has been mounted... This is a good preventative measure in handling long-term life of our systems...  

2. What ever percent is non-continuous has nothing to do with the hard-drive itself...  

3. If you want to check your hard-drive I would recommend running a program called "SpinRite" from Steve Gibson and check your drive.  This program will check the disk integrity and correct the errors on the disk itself...  

4. The operating system of Ubuntu is solid, it runs like a tank...  Pretty hard to self-destruct...  However, an upgrade to a newer version will have to take place eventually...   So, with the disk integrity in check, a clean install of a newer version when you so choose to do so...  Will keep Ubuntu running for many years...

Lastly, 
           The non-continuous file percentage should become problem between now and the upgrade...  Which should be no-more than 18 months from where we are today...

I hope this gives you some piece of mind and help develops some long-term strategies for you, while running the best open-source operating system available...

---

### Post by az on 2007-11-23
> **dpj23 said:**
>   This program will check the disk integrity and correct the errors on the disk itself...  

Badblocks is a command-line tool that is already installed on your system.  It can scan your disk for bad blocks.  It's free, unlike spinrite, which is proprietary.  

Spinrite claims to heal an unhealthy disk.  It may, but that has not been proven.  I reckon if a hard drive is starting to cause problems, it needs to be replaced to avoid data loss.  A new disk is the only way to guarantee that your data will remain safe.

> **dpj23 said:**
>  
4. The operating system of Ubuntu is solid, it runs like a tank...  Pretty hard to self-destruct...  However, an upgrade to a newer version will have to take place eventually...   So, with the disk integrity in check, a clean install of a newer version when you so choose to do so...  Will keep Ubuntu running for many years...

A fresh install does not check the disk surface.

And you don't need to do a fresh install, you can dist-upgrade from one release to the next.  You can have one install and dist-upgrade forever...

> **dpj23 said:**
>  
Lastly, 
           The non-continuous file percentage should become problem between now and the upgrade...  Which should be no-more than 18 months from where we are today...


The only time fragmentation will become a problem is when you start to run out of disk space.  You can run the same filesystem for years.  If you keep it less than 80 percent full, you will have little fragmentation.

---

### Post by linuxonbute on 2007-11-23
I think that unless you do get any obvious problems such as frequent file system checks on boot up you dont need to worry too much. Of course you should back up anyway.

I might easily be wrong ( my wife says I usually am )

I seem to remember reading many years ago when the IDE interface was young that I read that ide drives had a small portion of the disc free for re-mapping bad sectors and that was done by the disc itself.  If you get to the point where bad blocks are occurring regularly then I think it would be good to back everything straight away and get a new disc soon. 

Doesn't SMART offer some help with this?

---

### Post by dief-eh? on 2008-07-21
Hello,

Just checking in with additional info. I have a similar error message (see below),but *I* have 2.3% non-contiguous.(!) The additional info relates to the Seagate part of the story; I also have a Seagate drive that's less than a year old (Dec 27 '07)

> **linuxonbute said:**
> I think that unless you do get any obvious problems such as frequent file system checks on boot up you dont need to worry too much. Of course you should back up anyway.

Doesn't SMART offer some help with this?

And the second part of the story relates to the boot-up message that informs me that the SMART daemon is not on. I don't remember where I read about how to turn that back on, or why it's off when it used to be on. 

Any further info greatly appreciated!

Output of fsck, July 20/08: 

sudo e2fsck -f -C 0 /dev/sda1
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
/dev/sda1: 322887/19365888 files (2.3% non-contiguous), 
			11207904/38718650 blocks

---

