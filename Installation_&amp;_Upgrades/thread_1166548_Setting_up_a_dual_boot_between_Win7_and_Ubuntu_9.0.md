---
title: "Setting up a dual boot between Win7 and Ubuntu 9.04"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by The Funkbomb on 2009-05-21
Good day.

Let me explain my situation.  For the life of me, I cannot get Ubuntu to play nicely with Win7 RC 7001.

I use Windows for two things mainly: games and Photoshop.  I don't want to run Photoshop through WINE.  If I'm gaming or in Photoshop, sometimes I'll pop on the web, etc.

I use Ubuntu for just about everything else.  Most of the time I'm on Ubuntu but sometimes when I'm on Windows, it isn't worth it to just switch back.

I have a 750gb HDD.  In reality, it's 698.64gb.

SDA1 is the boot sector and it is 100mb of NTFS
SDA2 is ~100gb.  That is where I run Windows.  It is NTFS.
SDA3 is the rest and that's all Ubuntu and it is ext3.

This is what I want to do.

I want to make 4 partitions.

SDA1 will still be the boot.
SDA2 will still be Windows but a little larger ~200GB
SDA3 will be a share partition that will house all my music, movies, pictures, and firefox/thunderbird profiles.  This will be ~300GB
SDA4 will be my Ubuntu partition and will be ~200GB including my 5GB Swap.

My questions all pertain to SDA3.  Has anyone done this?  Set up a share partition?  Is this the way to go?

What File System should I use?  ext3 is out because Windows doesn't like it.  That leaves me with FAT32 and NTFS.

I know Ubuntu and Windows will both play ball with FAT32 but it isn't a good choice for a large partition.  What about NTFS?  Is that the way to go?

Thanks in advance.

---

### Post by Mark Phelps on 2009-05-22
Suggest you do the following:
1) Set up extended partition to hold additional partitions
2) Inside the extended partition, create the following:
-- NTFS partition for sharing data
-- Ext3 partition for Ubuntu
-- Linux-swap partition for swap

When you install Ubuntu, make sure that the ntfs-3g package is also installed so you can mount and use the shared partition.

---

### Post by The Funkbomb on 2009-05-22
Thank you for the reply.

Why, may I ask, should my NTFS share partition be in the SDA3 extended partition and not its own primary partition?

---

### Post by The Funkbomb on 2009-05-22
While I have you ear, I might as well ask this question.

Last night, I tried to partition my ext3 partition in a set up like you wanted using the live disk  It wouldn't work.  It told me to run fscdk -l or something like that.  I ran that and it passed except for something like .06 non-contiguous files.

Any way I can fix that instead of formatting everything?

---

### Post by The Funkbomb on 2009-05-22
Actually, nevermind.

I wanted to make the windows partition a little larger anyway.

---

### Post by The Funkbomb on 2009-05-23
Well, it was a struggle but I got it done.

I installed Win7 first and partitioned the drive so it was around 200gb and 100mb for the Windows boot.  Then I cut a 205GB chunk for Ubuntu.  I took that 5 gigs and partitioned that to make my linux swap.  What remained was 293.54.  I formated that as NTFS and labeled it Share.

This is what it looks like.

SDA1 Windows Boot.  100mb
SDA2 Windows 7.  200gb
SDA3 Extended
SDA5 NTFS partition labeled Share. 293.54gb
SDA6 Ext3 Ubuntu9.04 200gb
SDA7 linux swap 5gb.

It took me some time to get it right.  The worst part was partitioning after the Windows install.  That took about 2 hours just to partition it. :/

After that, the Windows boot was messed up.  I just popped the windows disk in and let it do the recovery.  I was convinced it was going to overwrite everything but it worked fine.

I used EasyBSD 2.0 Beta and set up my GRUB that I installed in SDA6.

Some good folks taught me how to fstab in the Ubuntu IRC channel and now my share drive mounts on boot.

It works beautifully.  I've put all my music, movies, pictures as well as my firefox/thunderbird profiles on SDA5.  I pointed them to the right folder on each OS and no issues so far!

---

