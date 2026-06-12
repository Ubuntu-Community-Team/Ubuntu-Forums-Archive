---
title: "Partition help!"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by celloandy on 2005-01-24
I started looking into Ubuntu a few months ago, and finally decided this weekend to make the switch from Gentoo.  I had had some questions about the transition, and posted them [here](http://ubuntuforums.org/showthread.php?t=4311&page=1).  In particular, I had made the mistake when setting up my Gentoo partition structure with one big root partition (no separate home), so I wasn't quite sure how to install Ubuntu without cooking all of my data.  My current structure is as follows: sda1 is a 10G WinXP partition, sda2 is a ~128M /boot partition (was ext2), sda3 is a 2G swap partition, and sda4 is a ~105G root partition.

The suggestion given in response to the forum post was for me to boot with a Gentoo boot disk and delete everything but the home directory, then to select the option to keep the data and use the partition when I did the Ubuntu install.  I went ahead and did all of the deleting, leaving me with just a home, and booted the Ubuntu installer.  Everything went well initially, and I configured the partitions to wipe sda2 (boot), and reformat it as ext3, to leave sda1 alone, and to keep but not format sda3 and sda4.  When I hit "continue, it formatted sda2, then spat out some warning about how the layout of my ext2 partition was unusual (which is weird, since I no longer had any ext2 partitions).  I could either go back or continue, so I continued.  Another box came up that said that there were uncorrected errors on sda4 (the header of the box said something about resizing not being implemented, but I didn't want to resize anything!), and that I wouldn't be able to use the partition at all unless I went back and corrected the errors.  I went back, but saw no errors to correct, so I thought maybe there was a problem with the filesystem.  I rebooted back to Gentoo, and checked that the partition mounted and unmounted (it did), and I fscked it as well.  The Ubuntu installer did the exact thing the second time, as well as the third.

At this point, I have no functional Linux install, and since Ubuntu ate my /boot partition before it gave me the error the first time, I don't have a bootloader to get to my XP partition, either, so I'm living off of Gnoppix, which is a little unpleasant.  Any help/suggestions anyone has would be enormously appreciated.

Andrew

---

### Post by celloandy on 2005-01-25
*shameless bump*

Does no one have any idea?  I'm getting a bit desperate...

Andrew

---

### Post by rudi on 2005-01-25
This is a wild guess, and i haven't tried it myself, and i don't know if it should work :P but...

Could you first convert your partition to ext2 using tune2fs to disable journalling, then use a tool like partition magic to resize your partition and create a new one, turn journalling back on, and install ubuntu in your freshly created partition?

It is just a wild guess, and please correct me if i'm wrong. I'm not a fan of partition resizing, but as your option runs out it may save your precious data ;)

Good luck with it

---

### Post by celloandy on 2005-01-25
That's a possibility.  How safe would that be?  Also, at present, I have four partitions, so if I added another one, would I need to deal with the whole logical/extended thing?  Because that could be unpleasant, and I'm not sure how partition magic would deal with it.  Anyone else know anything about this?

Andrew

---

### Post by rudi on 2005-01-26
Well, i think you mean you have four primary partitions? Ranish partition manager can create up to 31 primary partitions, and it features partition resizing.  Take a look at [http://www.ranish.com/part/](http://www.ranish.com/part/). If i am not mistaking, fdisk (windows partitioning tool) can only handle a few primary partitions, but the last time i'd let windows partition my disk was.. well, long ago :-P

I can't answer your question on how safe it is, i don't like the idea to resize, but if it really was that much of a risk, why would so many programs feature it? If you don't have the possibility to backup your files on DVD/CD, this might be worth a try, but i'm no expert on this, so anyone can correct me if i'm wrong.

---

### Post by celloandy on 2005-01-26
So it as it turns out, partition magic can convert a primary partition into an extended partition with a logical partition inside it, and also does safe resizing.  I rearranged things a bit, and did the resizing and so forth (which took a few hours), and tried the install again.  It still complained about what is now my home partition, saying it had a strange layout, so I left it alone, then added it as the /home partition by manually tweaking the fstab post-install.  This worked just fine, but it felt a bit hackish, so perhaps if any devs are reading, this might be something worth investigating, as this probably isn't something that should happen.  I don't think that it's worthwhile for me to file a bug report or anything, since I probably couldn't give enough of the necessary specifics for this problem to be reproducable, but that's what I know.

Anyway, I now have a functional Ubuntu install, with my old data preserved, so I'm happy.  Thanks for everyone's help!

Andrew

---

### Post by rudi on 2005-01-26
Great it worked out! Cheer cheer :-P

---

