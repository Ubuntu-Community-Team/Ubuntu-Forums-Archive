---
title: "Help with flash drive"
date: 2011-05-26
forum: Hardware
---

### Post by klambert2010 on 2011-05-26
I installed ubuntu on my 8 gig flash drive and told it to use the whole drive.  Instead it used 3.9 gigs for my installation and has 4.3 gigs as extended and swap space.  How do I get that part back to use as part of the main drive?

---

### Post by ILoveYorkies on 2011-05-26
[SIZE=3]Hi there,
If you don't have alot of ram then you need a swapfile. I've heard the  rule is at least twice the swapfile as you have ram so if you have 1 gb  ram you should have at least 2 gb swapfile. 2 gb ram=4 gb swapfile, etc.  That's probably why it's used that 4.3 gb because, it thinks it needs  it. The swapfile makes Ubuntu faster and leaves room for your ram to do  other things at least that's what I understand but I could be wrong  since I'm new to Linux myself. You could go to apps then to disk utility  and try to resize the swapfile partition to make it smaller on the  flash drive then format the unallocated  space so it's usable to you.  BUT BE CAREFUL RESIZING OR REFORMATTING. YOU COULD LOSE DATA ON IT OR  MAKE THE FLASH UNBOOTABLE!!  READ any help files you can find on  formatting and resizing partitions. MAKE SURE YOU ARE RESIZING AND  FORMATTING THE CORRECT DRIVE BEFORE GOING THROUGH WITH IT SINCE ANY APPS, PERSONAL DATA WILL BE ERASED! Many people have formatted the wrong drive and lost all their personal files like music, videos, documents, passwords, even the whole os leaving the computer unbootable.

You could use disk utility to check on the extended partition if there isn't any data on it other than the swapfile which should be in a partition by itself and the swapfile doesn't take up all the space in the extended partition then using disk utility you could make a logical partition or disk utility may call it a volume instead of partition but again BEFORE RESIZING OR FORMATTING ANY PARTITION OR VOLUME MAKE SURE IT"S THE CORRECT ONE! I can't stress that enough. READ UP ON HOW BEST TO DO IT FIRST SO YOU DON"T HAVE TO READ UP ON  TRYING TO RECOVER FROM A MISTAKENLY FORMATTED DRIVE! 
Best of luck.
[/SIZE]

---

### Post by oldfred on 2011-05-26
As long as the partitions are not mounted you should be able to use gparted to resize the partitions.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

I have 4GB of RAM and while my normal installs have 2 to 4GB of swap, my install to a Flash drive has no swap at all.

You do want to reduce writing as much as possible as flash writes are slow.
It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

### Post by oldfred on 2011-05-26
@       ILoveYorkies
Some now prefer swapfiles over swap partiitons, but the rules on size have been updated with systems with lots of RAM. If over 1GB of RAM you can use swap =2GB unless you want to hibernate. Then you have to have swap as large as RAM in GiB or a little more than GB. If you only have 512MB then swap should be twice RAM.

One cannot have enough backups and we have to keep encouraging users to make it part of a regular procedure. Often users make mistakes and that is when a backup really comes in handy. I am afraid I know from experience.


HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by klambert2010 on 2011-05-27
Okay so I have 4 gigs of ram in my laptop, I think that is plenty, so I really don't need the swap part, right?  Or am I understanding it wrong?

---

### Post by oldfred on 2011-05-27
You can get by without swap. Unless you are planning on running every application while editing videos. (Which i would not even attempt from a flash drive install).

Realize a flash install is slow both due to USB port being not as fast as IDE or SATA and flash drives not writing as fast. With writes minimized it can be a functional system. My flash actually boots about as fast as my hard drive, but with hard drive I mount a bunch of partitions and some are NTFS which are always slow to mount. Larger applications may be a bit slower if compared to a hard drive.

---

