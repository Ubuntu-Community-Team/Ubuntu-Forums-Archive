---
title: "Replacing a failing Harrd Drive"
date: 2012-10-17
forum: Hardware
---

### Post by gorellana09 on 2012-10-17
Hello folks, 

I am hoping someone here can give me some advice. I have a badly failing Hard Drive on my laptop. I am now having to run badblocks every two days (yes it is bad). So before it dies for good I want to replace it. It is a Western Digital WD2500BEVS-60UST0 SATA 2.5" 250GB. 

Two critical questions: 

1.If I am going to replace it I might as well replace it with one of more capacity? I am triple booting Win Vista, Xubuntu, Mint so one with more capacity would be great. My fear though is will my laptop support a different hard drive or will I have to replace it with the same type and model that is there now? 

2. How do I transfer all my files to the new hard drive without having to re-install my OS's primarily Windows Vista as I don't have a disk for it only the system recovery partition that comes with the laptop. My linux partitions I am not worried about since it is easy to install a fresh copy.

Any advice and help would be greatly appreciated, as you can see I am not that tech smart.

---

### Post by PowerBarry43 on 2012-10-17
Hi

I would recommend buying a new hard drive such as this one

[http://www.ebuyer.com/255282-wd-500gb-black-mobile-drive-wd5000bpkt](http://www.ebuyer.com/255282-wd-500gb-black-mobile-drive-wd5000bpkt)

its made by the same company as your current one and normally hard drives are fairly interchangeable, in the old days compatibility issue could happen but very rarely in recent years will a hard drive be totally incompatible. It's also a 500Gb hdd rather than a 250Gb one which isn't massive these days and the price difference between the two really isnt that large. As for copying the OSes from one drive to the other you can use a program called clonezilla [http://clonezilla.org/](http://clonezilla.org/) to backup your hard drive and restore it to the new one although you will need some form of external storage for that and I strongly recommend reading about clonezilla a lot and maybe watching a few youtube videos of people using it so you get a feel for what you're doing.

Hope this helps!

Barry

---

### Post by gorellana09 on 2012-10-17
Thanks for your reply Barry. When you talk about incompatibility with older systems, how old do you mean? My laptop is 4 years old now and I know I should replace the thing however at the moment it is much easier for me to afford 60$ - 100$ on a hard drive than spend 4 times as much on a new computer so I will try and get as much life out this poor laptop as I can.

---

### Post by offgridguy on 2012-10-17
I would recommend a complete backup of all your data, before your drive fails completely.  If you don't already have a system restore disk for your vista, then make
one .
As to the hard drive, a new replacement obviously has to be compatible with your 
computer, however you can probably find one with a lot more storage space than
you have now.  I would recommend ebay  { yep good ol ebay }.  I have purchased new
hard drives on ebay from this seller  memorylabs, try that or memory labs {46654 .
I have no complaints about this seller, replaced my 240 gb. drive with 350, they also had
500 gb available.:)

---

### Post by TheFu on 2012-10-17
Get a drive that is the same size or larger AND matches with 512b or 4K sector sizes.
Then use a liveCD to boot with both the old and new disk connected.
The use dd or dd_rescue to mirror the entire disk device exactly.  Do this at the HDD level (/dev/sda), not the partition (/dev/sda1) level.

That will mirror, bit for bit, everything on the source HDD, including grub, vista, and any other OS on the disk.

Then swap the new drive into the laptop and boot each OS.  I doubt any of them will notice a difference, except perhaps Vista. You might need to let it fix the broken install, but that should be it.

If you got a larger HDD, now you can move the partitions around and increase or add any more storage where you like. For Windows, it is best to use Window partition tools to touch it. For all other OSes, use gparted - including moving the Linux partitions out of the way so that Window partition manager can be used later.

Badblocks are ... er ... bad.  I hope you have a great backup strategy that works and does daily, versioned, backups.  Something will help fight corrupt files.

---

### Post by gorellana09 on 2012-10-17
Thanks for all the replies guys. @TheFu, how do I know if a drive matches with 512b or 4K sector sizes? I have been looking at the one recommended by Barry WD Scorpio Black 500 GB SATA 7200 RPM 16 MB Cache Bulk/OEM 2.5" Mobile Hard Drive (WD5000BPKT) it is only $60 on Amazon so that's not bad, and I like the fact it says it is good for power computing. 

As for a backup I have an old 160GB HD on an enclosure USB Kit I use for saving all my important files. My Win Vista stuff like downloads, documents, pics, etc. are saved automatically to it and not the internal HD. And on my Linux partitions I make periodic backups as well. My only concern is the OSes themselves but from what I am reading it should be easy clone the drive. 

About badblocks, no kidding, I am running the test right now and already found 32 errors, so my guess is this hard drive has only hours to live. 

Question to all since you all seem knowledgeable on the topic. Why do you think I only keep getting problems with my main Linux partition with 60GB? My Windows partition with 150GB or so boots fine (although slow) and seems to have no problems. My third and smaller partition which I use for testing distros is only 10GB and I also don't seem to have much of a problem with badblocks.

---

### Post by ahallubuntu on 2012-10-17
No need to get one of the same size and manufacturer.  Get any drive that's compatible and fits.

However, your existing drive does use 512b sectors ("old style"), and most new laptop drives are "advanced format" 4K byte sector drives as mentioned earlier.  An advanced format drive should actually work fine, except that you would need to align all of the partitions to 4K sector boundaries to achieve the best performance.  This is pretty easy to do if you do it right.

Here's how: clone each partition one at a time using gparted by first creating new partitions on the new drive; Ubuntu starting with 11.04 should automatically created aligned partitions.  (Use a live CD 11.04 or newer to clone, anyway.)  Gparted allowed copying/pasting of partitions individually - even Windows partitions - and it worked well for me recently when I cloned my XP + Ubuntu drive to a larger one.

However, I would be much more worried about failed sectors causing errors in the copy.  In that case, you should probably use ddrescue to copy each partition, but you can still create the new partitions first with Gparted with Ubuntu 11.04 or newer so the partitions are aligned.

---

### Post by ahallubuntu on 2012-10-17
> **gorellana09 said:**
> Question to all since you all seem knowledgeable on the topic. Why do you think I only keep getting problems with my main Linux partition with 60GB? My Windows partition with 150GB or so boots fine (although slow) and seems to have no problems. My third and smaller partition which I use for testing distros is only 10GB and I also don't seem to have much of a problem with badblocks.

Bad sectors may be on one part of the drive and not the others, causing you more problems with one OS than another.  The drive surface may be failing just on one part of the drive, and that could cause some sectors to fail completely, others to be very slow to access.

---

### Post by TheFu on 2012-10-17
> **gorellana09 said:**
> As for a backup I have an old 160GB HD on an enclosure USB Kit I use for saving all my important files. My Win Vista stuff like downloads, documents, pics, etc. are saved automatically to it and not the internal HD. And on my Linux partitions I make periodic backups as well. 

I need to point out that a "backup" means you have the data in at least 2 places.  That external drive you are using for "backups" can also fail at any time.  Having 5+ copies of really important data is a good idea.

**All hard disks will fail.  All of them.**  The goal is to have them fail either when you don't care anymore or when you stopped using it.  A HDD failing is like death - you and I will eventually die. That is 100% certain.  Your HDDs will fail. That too, is 100% certain.

I see that someone else addressed the 4K sectors.  I have a few drives with 4K sectors, but I have not cloned data, boot sectors, partitions onto them.  I used rsync to mirror data over.  This is a much higher level process than dd, so I don't trust it to place critical files in exactly the needed locations requirement for booting.

---

### Post by gorellana09 on 2012-10-27
Hello guys quick update to this thread and more help needed. I finally  got around to getting my new Hard Drive (it came in the mail today at a  great time as my preset hard drive didn't let me boot this morning  again!). I got the one suggested by PowerBarry43 on the second post. 

@Ahallubuntu, my question. You say to copy each individual partition in gparted? I checked and yes gparted does seem to have a copy and paste feature. 

Here is the output of fdisk -l:

```

geo@geo:~$ sudo fdisk -l
[sudo] password for geo: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb53a46d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   308254719   154127328+   7  HPFS/NTFS/exFAT
/dev/sda2       468482048   488390655     9954304    7  HPFS/NTFS/exFAT
/dev/sda3       308256766   468482047    80112641    5  Extended
/dev/sda5       308256768   436248575    63995904   83  Linux
/dev/sda6       464347136   468482047     2067456   82  Linux swap / Solaris
/dev/sda7       436250624   458582655    11166016   83  Linux
/dev/sda8       458584064   464343039     2879488   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
geo@geo:~$ 


```As you can see my present HD is very messy. I have 2 swaps (no idea why) and also 2 unallocated partitions which are not showing there which are less than 1GB each.

- The second reading is my new hard drive. Everything seems to be identical but why is Disk identifier showing nothing?

- What is a partition table? and how do I create one? Gparted has a thing that says create a partition table.

- If I copy each partition one at a time can I copy only 1 swap and have my two Ubuntus share the same sawp?

Any help and advice will be great before I attempt to do anything that may break my system for good.

---

### Post by chief10 on 2012-10-27
Before you do anything else make sure you back up all of your stuff right now. In fact don't turn that computer on until you're ready to back it up.

---

### Post by gorellana09 on 2012-10-27
Yep, doing that already :)

---

### Post by ahallubuntu on 2012-10-27
Start up Gparted and create new partitions (in the scheme you want) on the new hard drive.  When you do, Gparted will first want to create a partition table on the new disk, and then everything will appear normal with fdisk.  Brand new disks don't have a partition table much of the time because they are empty.

I'm not sure what extra (small) partitions you are referring to on the old disk?  FYI, the Extended partition (sda3) is just a container partition for all the logical partitions inside of it.  The original DOS spec allowed a maximum of four primary partitions; the Extended partition was a hack to allow you to add more than four (logical partitions).  Ubuntu doesn't care whether partitions you use are primary or logical, but Windows may care; as a rule, I try to put Windows boot partitions as primary partitions.  NTFS partitions that are data-only can be logical partitions.

You can try copying-and-pasting partitions with Gparted, but if there are errors (bad sectors) you might not be able to complete the operation.  In that case, try ddrescue.  Make sure to make the new partitions you are copying to at least as big as the original.

No need to copy swap partitions.  Just create them.  They'll have new UUID numbers - you can find out what they are with the "blkid" command.  Then you can modify your fstab on the new disk to use those new UUIDs to point to the the swaps.  (And to the other mounted partitions in fstab.)

Make sure you use at least Ubuntu 11.04 or newer Gparted to create the partitions so they will automatically be aligned to a 2048 byte boundary on the new advanced format drive you bought.

Yes, you can probably get away with just one swap partition.  One potential benefit of two separate swap partitions instead of sharing one: you could hibernate one Linux distro and boot the other one, then go back later and resume the first one.  Can't do that if you share a swap partition between them.  Maybe you will never do this so won't care.

---

### Post by gorellana09 on 2012-10-28
Thank you all for all the help Gparted worked well but as expected the damaged partition gave a lot of errors and kept aborting the process, so I decided that as long as the Windows partions had been copied without a problem I would just create new partitions for my ubuntu installs and install them fresh.

So what I did was create my extended partition and created my partitions for my Ubuntu and Linux Mint in there. Then did a fresh install for them. Computer boots, all OSes boot, except Windows cried on the first boot about system changes and forced a disk check but after that everything worked fine. 

The only problem is that after all was said and done I now get a warning about an internal battery needing replaced? Does anyone know anything about that? Should I worry?

---

### Post by ahallubuntu on 2012-10-28
Battery warning is probably coincidental.  Laptop batteries last only a finite amount of time, sometimes only a year or two.  Maybe it's just time to replace yours?  I find them cheaply on eBay myself.

---

### Post by gorellana09 on 2012-10-28
It says something about internal battery though. The message comes out before GRUB

---

### Post by ahallubuntu on 2012-10-28
Every computer (even a desktop) has a little CMOS battery inside of it, in addition to the regular battery a laptop would have.  But I've yet to ever see a computer warn me about a low CMOS battery.  I don't know what make/model of laptop you have, so I have no idea what issue you might be seeing.  If you suspect it is related to the new hard drive, swap the old one back in.  Could be the warning has been there for a while but Grub the way it was previously installed was masking the warning?  I'm just speculating here, as I don't really know what you are seeing...

---

### Post by alkh3myst on 2012-10-29
I see you're not that comfortable with "going under the hood", and you're afraid of making a critical error. I understand, I was you once. This company makes a very painless HD cloning kit, which afterward doubles as an enclosure for an external HD: [http://www.apricorn.com/](http://www.apricorn.com/)

Their upgrade kits ([http://www.amazon.com/Apricorn-EZ-UP-UNIVERSAL-Upgrade-Universal-Notebook/dp/B00009WQS1](http://www.amazon.com/Apricorn-EZ-UP-UNIVERSAL-Upgrade-Universal-Notebook/dp/B00009WQS1)) do all the work, with a minimum of input from you. Shop around, you can probably find it cheaper (newegg, etc.), but if time is a premium, Amazon has very fast premium shipping options, that you can often get at discount.  

As for capacity, *always* replace your old drive with a larger one. Each new OS version and new versions of software require larger storage. Plus, prices for hardware are always falling, and there's eventually going to come a time when HD prices will go into a freefall, once SSDs (flash drive hard drives) reach market saturation. 


:popcorn:

---

### Post by gorellana09 on 2012-11-01
The battery warning was from HP and it was about my laptop's battery. So I am marking this thread as solved. Thanks everyone for all the great help, I am now enjoying my new bigger hard drive :D

---

