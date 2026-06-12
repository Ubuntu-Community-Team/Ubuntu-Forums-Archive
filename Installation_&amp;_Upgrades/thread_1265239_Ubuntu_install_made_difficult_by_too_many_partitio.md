---
title: "Ubuntu install made difficult by too many partitions"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by DeclanMcErlane on 2009-09-13
Hey,

Got a new laptop the other day from Dell and I'm trying to create a dual-boot setup like in my old desktop; Vista (upgrade to Windows 7) and Ubuntu.

The problem is that when I fresh-installed Vista to get rid of all the bloatware from Dell I created 3 partitions to make defragmenting the OS that wee bit easier whenever the time arises!
[LIST=1]
[*]80GB - Windows OS and Programmes
[*]60GB - Games
[*]3xxGB - Documents
[/LIST]

I left about 10GB free for my Ubuntu partition but during the install phase it said the partition was "unusable" so I did a bit of google-ing. Turns out you can only have 4 primary partitions on a HDD and, when I took a look at the HDD using GParted, there was small 30MB partition called Dell Utility created before my 80GB OS partition.

Long story short; how can partition my HDD to allow me to have this sort of setup?:

[LIST=1]
[*]100GB NTFS - Windows OS & Programmes
[*]100GB NTFS - Games
[*]250GB NTFS - Documents and Downloads etc
[*]20GB - Ubuntu (inc. swap)
[/LIST]

Many Thanks,

Declan.

---

### Post by Partyboi2 on 2009-09-13
Hi, you can create a extended partition to get around the 4 primary partition limit.
So create as your 4th partition a extended partition.

---

### Post by DeclanMcErlane on 2009-09-13
Could you elaborate a little, specifically how it would apply to me?

---

### Post by Partyboi2 on 2009-09-13
Ubuntu needs 2 partitions to install one being the / (root) partition and the other one being the /swap partition. Because you already have 3 primary partitions you cannot install Ubuntu using primary partitions without removing one of your current partitions. But you can get around this by creating a extended partition, once you have created a extended partition you can have as many logical partitions as you like. 
This means that Ubuntu will be install on 2 logical partitions, as well as you now can create in the future more partitions if you need them.

1. 100GB NTFS - Windows OS & Programmes       (Primary)
2. 100GB NTFS - Games    (Primary)
3. 250GB NTFS - Documents and Downloads etc (Primary)
4. Extended Partition
4.a 20GB - Ubuntu (Logical)
4.b /Swap Partition (logical)

---

### Post by newsoft on 2009-09-13
> Could you elaborate a little, specifically how it would apply to me?


Yes, please explain more

---

### Post by DeclanMcErlane on 2009-09-13
That's a wee bit easier to understand. Can I use GParted on the Ubuntu Live CD or do I need to create a Live CD of GParted to create these partitions. I'll do a wee bit of googling on extended partitions as I've never created one before. My thanks to Partyboi2 :]

EDIT: Quick question: Why would I make the Documents and Games partitions primary and not extended? And if I install Ubuntu on an extended partition does this not mean the OS won't boot? I'm taking this from this site.
[http://www.theeldergeek.com/hard_drives_07.htm]("http://www.theeldergeek.com/hard_drives_07.htm")
> I've never found there to be any difference in how the two types operate, other than the fact you can start operating systems from Primary partitions where that isn't possible with an Extended partition.

---

### Post by Partyboi2 on 2009-09-13
I don't use Vista but I  have read that you will need to use a 3rd party partitioning tool to create the extended partition. Some people in the past have had problems using gparted with Vista, so I would suggest going to the [[COLOR=Blue]gparted website [/COLOR]]("http://gparted.sourceforge.net/")and downloading the latest version and burn it to a disk. Then boot the gparted live cd and create a extended partition. Its pretty much the same way you create a primary partition except you are choosing a extended one.

---

### Post by Partyboi2 on 2009-09-13
> **DeclanMcErlane said:**
> That's a wee bit easier to understand. Can I use GParted on the Ubuntu Live CD or do I need to create a Live CD of GParted to create these partitions. I'll do a wee bit of googling on extended partitions as I've never created one before. My thanks to Partyboi2 :]

EDIT: Quick question: Why would I make the Documents and Games partitions primary and not extended? And if I install Ubuntu on an extended partition does this not mean the OS won't boot? I'm taking this from this site.
[http://www.theeldergeek.com/hard_drives_07.htm](http://www.theeldergeek.com/hard_drives_07.htm)
You can make Documents and Games a logical partition, I was under the impression you were leaving the first 3 partitions as they are. 
Ubuntu works fine installed on logical partitions. From what I have read in the past Windows does not like being on logical partitions, so keep your Windows on a primary partition.

Edit: If you are going to start from scratch you could use something like
Partition 1 (primary) Vista
Partition 2 Extended partition
Partition 3 (logical) 100GB NTFS - Games 
Partition 4  (logical) 250GB NTFS - Documents and Downloads etc
Partition 5  (logical) Ubuntu /
Partition 6 (logical)  /swap

---

### Post by DeclanMcErlane on 2009-09-13
Primary or logical for the Documents and Games partitions doesn't really matter too much. I was just using the site I linked earlier as a reference because he/she used an extended partition for their documents.

But anyway. Aye, I'll download the GParted Live CD and get a-formatting using the list you described in your second post. I'll keep you informed as to how it goes.

---

### Post by raymondh on 2009-09-13
EDIT : I Type slow ...... you can put games and docs inside the extended as partyboi2 says.

---

### Post by DeclanMcErlane on 2009-09-13
Okies dokes. All done :]

My HDD is partitioned as follows:

/dev/sda1: 100GB - Vista and Programmes
/dev/sda2: 100GB - Games
/dev/sda3: 250GB - Documents
/dev/sda4: 15GB - Extended partition
+ /dev/sda5: 7GB - Ubuntu 9.04 (logical)
+ /dev/sda6: 8GB - Swap area (logical)

Thanks for all the help guys, especially Partyboi2. Is there a thank button and a way to mark this as [SOLVED]?

---

### Post by Partyboi2 on 2009-09-13
Your welcome, good to see it all went well. :) There use to be a thank you button awhile back but it was removed as it was causing problems with the database. You can mark your thread solved by going to "Thread Tools" on the top right of the thread and selecting from the menu "Mark this thread Solved"

---

