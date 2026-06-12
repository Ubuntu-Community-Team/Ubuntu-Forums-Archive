---
title: "How can I install Ubuntu on XFS file system?"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by psychok9 on 2009-02-04
Does it exists a correct procedure to install Ubuntu on the XFS file system?
I've tried a lot of times without any success (error 17 grub).
I've tried a ext3 /boot partition and it's the same thing.

---

### Post by inobe on 2009-02-04
this says it will work

[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

the fact that you have grub issues points to hardware and bios configuration.

how are they set ?

i have experienced these problems

changing the drive from raid to ide in the bios

what type of hard drives are you using, include if this involves raid and dual booting

if you have sata's, remove one from the configuration, try to narrow out anything that will interfere with your setup.

ide hard drives should have correct jumper setting, they should also be on the correct ide channel.

---

### Post by buntunub on 2009-02-04
I dont think xfs is available as an install option for live cd. I got it all working fine pre partitioning via gparted prior to install using ext3 on /boot and xfs on the partitions that needed it. Works like a champ. I do recall that I had to install the xfs filesystem utils to get it all to work right though. I would not recommend xfs for /home, /, /usr, or any other partition that uses small files. ReiserFS or ext4 would be far more appropriate for those. I actually use xfs for my Mythtv server because xfs was designed to handle those types of massive file types.

---

### Post by dabl on 2009-02-04
Yes, you can.

HOWEVER, my own experience is that XFS is not a good filesystem for the root filesystem.  It lasted 6 months and then began to act flaky -- my VMware VM started taking way too long to shut down, and there were other signs of trouble, so I reinstalled on ext3.  However, I have some large (250G) data partitions that are XFS, and it seems to be OK for that application.

---

### Post by psychok9 on 2009-02-04
I don't think it's a bios problem, the installation works correctly when I format the root partition with ext3.
Workaround /boot (ext3, root (xfs) seems not to work.
I've tried last time with the Alternate CD (it works on another couple of raid 0 hard disks), but I've the similar problem:
Lilo and Grub can't install on /dev/sda or /dev/sda1.
This is a normal SATA drive (not raid).
Can I try Grub2 or a newer boot program? I'm very tired of a lot of slow installations without any success...

I've read the XFS features and I would like to try it.
Thank you in advance.

---

### Post by psychok9 on 2009-02-04
I can't understand this (a bug?):
[[IMG]http://img262.imageshack.us/img262/4725/immagineva7.th.jpg[/IMG]](http://img262.imageshack.us/my.php?image=immagineva7.jpg)

---

### Post by dabl on 2009-02-05
If you really insist on installing on an XFS filesystem, use a GParted Live CD to format the partition first, then use Live or Alternate Ubuntu CD to install on it.

You'll need a separate small partition for /boot -- 100MB is plenty big enough. That one must be formatted ext3.

Then use "manual" partitioning during *buntu installation, and set the mount points for the "/" and "/boot" partitions.  Should work.  Here's my notes from a couple of years ago:

[http://kubuntuforums.net/forums/index.php?topic=3087434.0](http://kubuntuforums.net/forums/index.php?topic=3087434.0)

Reminder:  it fell apart after less than 6 months of use.  :?

---

### Post by psychok9 on 2009-02-05
> **dabl said:**
> If you really insist on installing on an XFS filesystem, use a GParted Live CD to format the partition first, then use Live or Alternate Ubuntu CD to install on it.

I've tried it, but the CD Alternate tell me that XFS fs active options aren't compatible.
I've format again my Samsung 500Gb SATA from alternate CD partition menù:
[[IMG]http://img214.imageshack.us/img214/9427/schermatadevsdagpartedur6.th.jpg[/IMG]](http://img214.imageshack.us/my.php?image=schermatadevsdagpartedur6.jpg)
This a "view" from another raid hdd and ubuntu installation.
> 
You'll need a separate small partition for /boot -- 100MB is plenty big enough. That one must be formatted ext3.

Then use "manual" partitioning during *buntu installation, and set the mount points for the "/" and "/boot" partitions.  Should work.  Here's my notes from a couple of years ago:

[http://kubuntuforums.net/forums/index.php?topic=3087434.0](http://kubuntuforums.net/forums/index.php?topic=3087434.0)

Reminder:  it fell apart after less than 6 months of use.  :?
This is the final result :(
[[IMG]http://img24.imageshack.us/img24/2634/0502091819nf8.th.jpg[/IMG]](http://img24.imageshack.us/my.php?image=0502091819nf8.jpg)

What did it fall apart after less than 6 months of use?
Has the filesystem XFS been corrupted? :o 
Thank you very nice for your help, is very appreciated ;)

p.s. Now i try to remove 2 my Raid hdd and stand alone the sata samung 500gb.

---

### Post by dabl on 2009-02-05
> **psychok9 said:**
> 

 the CD Alternate tell me that XFS fs active options aren't compatible.



Hmmmm -- this may be something new since I installed on XFS.  There were no "objections" from the installation CD, in my case.  I installed on a WD1500 Raptor hard drive.


> 

What did it fall apart after less than 6 months of use?
Has the filesystem XFS been corrupted? :o 



I'm not a filesystem developer, so I can't give a high-precision answer.  I have a VMware Win XP virtual machine, about 8G in size, that runs a customized MS Visual FoxPro database.  After about 5 months, I noticed that when I closed the VM, it seemed to take longer than usual.  Within a couple more weeks, it was taking 10 minutes to close, with constant disk activity the whole time.  The xfs-progs utility showed it 34% fragmented, and when I ran the defragmenter, it would not reduce the defragmentation below about 30%.  At that point I decided I could not risk my data any more, even though I made backups daily, so I re-installed.

I also have a WD7500 that is partitioned in 3 XFS partitions about 250G each, and on those partitions are data that does not change much (videos, images, music, etc.).  As far as I can tell, there is no problem with those filesystems -- I don't change the data very much, and there is not much fragmentation.

FYI, I am presently running Kubuntu 8.10, including my VMware Player VM, on a JFS filesystem, and it seems to be fine.  It has been running since 8.10, Alpha 5 -- I think it was installed in September.

---

### Post by inobe on 2009-02-05
had a friend that lost his myth setup, happened last year, he still complains about it to this day.

i don't know what happened exactly, the fella is into development' so that has to say something .

good luck

---

### Post by buntunub on 2009-02-05
XFS is primarily a file system that was designed to handle best files that are mammoth in size. Things like huge chunks of video, TV recordings (ie Mythtv servers), specialized file servers.. Things of that nature. XFS was never designed for regular Desktop Linux uses, and thus, does not handle small files well at all (files less than 1GB in size, for example). This is exactly why everyone who has responded to this thread has recommended that you DO NOT do what you are attempting to do. ReiserFS, ext3 (on pre 2.6.28 kernels), and definitely ext4 on .28+ kernels. Btrfs also shows a lot of promise but that is still some ways away from being stable yet. JFS is also a very good file system, but it does not stack up well on cross comparison filesystem tests vs. ext3, and definitely ReiserFS, which is currently the king of Journaled file systems for smaller files, at least until Jaunty/F11 release cycles come around, at which time ext4 will become the new default filesystem. With all that said however, should you choose to still persist in installing Ubuntu on XFS, then you can try [this]("http://www.faqs.org/docs/Linux-HOWTO/Linux+XFS-HOWTO.html"). Do let us know how that works out for you.

---

### Post by psychok9 on 2009-02-05
You have persuaded me. I'm find a "great performer" file system... but "**safe**", and with mixed situations: very big files (iso DVD file, very large backup archive file of my system... etc) and little files (music, and general system files).
I've noticed choppy performance of my system when I transfer very large or a lot of files and I'm found on the XFS performance my answer (before your warnings). I can't understand if is the result of an excessive usage of my cpu of the fakeraid driver or ext3 security features or is the maximum that I can get and I need a new disk :)

My source of XFS info is [here]("http://www.debian-administration.org/articles/388").

ReiserFS seem to be better for small files, and last JFS i don't have info of security/performance...
Ext3 seem to be the choice for now...
You know tricks/tips for improve ext3 performance?

Anyway,
today I've tried with success, on 500Gb hdd in a "test" partition, last Jaunty with Ext4 file system... and like it, seem to be a good and fast file system (1st look and I'm not a file system expert).

Thank you very much :popcorn:

p.s. This is my spec:
Q6600@3.240GHz, P5Q Deluxe with last bios 1702, 4Gb DDR2, Zotac 8800 GT AMP!, 2xSeagate 160Gb, 1xSamsung 500Gb HD501JL.

---

### Post by gfxfreak on 2009-02-24
Although late but here is my advice:

DO NOT mount / on any XFS partition. I did it and it wiped out my 250 GB hard disk with a seek error.

my 2 cents

---

