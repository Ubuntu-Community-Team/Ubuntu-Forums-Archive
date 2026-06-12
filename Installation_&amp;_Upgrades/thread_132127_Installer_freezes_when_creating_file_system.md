---
title: "Installer freezes when creating file system"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2006-02-17
I'm trying to install Ubuntu 5.10 on a 200GB disk.
It all works well until the partitioning phase.

I select "Erase all space of /dev/hda" (or whatever it says) and the partitioner suggests two partitions.

When go ahead and create the partitions the disk starts to set up the filesystem.

But the progress bar always freezes after a short while! Sometimes a 2%, sometimes at 8% etc.

Just to test the disk, I installed Windows XP on it. That worked well.
Then I tried to install Ubuntu once more: yet another freeze!

What's going on?

---

### Post by Installer36 on 2006-02-17
I encountered the same problem last night .I had Xp and Ubuntu and after doing some "learning " in Linux I decided to reinstall Ubuntu.When I got to the partion part of the install I deleted the two existing Linux partions and choose to let the install repartition. All went well until about 6% of creating the file system. Not knowing what to do I put the Kubuntu Cd in and got the same errror. My only way around was to erase all the hard drive and start over with a fresh drive. This is probably good for me because I keep reverting back to Xp when I cant figure something out in Linux. Now what caused it I have no idea or what the solution should have been . I know this isnt any help but this is the place for help with Ubuntu. Good luck...Installer36

---

### Post by silversphere on 2006-02-17
Hi I had similar issue well. it didn't freeze but the install was broken. This happened on Red hat too. The reason I believe is to do with detecting hard drive parameters correctly, there is an option about special parameters or special hardware you need to tick that and hopefully all will be fine:p

---

### Post by aysiu on 2006-02-17
Freezing during installation usually indicates that you either have a hardware problem (something wrong with your hard drive or CD-ROM drive) or that you have a corrupted CD (corrupted during download or corrupted during burning).

It's probably the latter. This link may help:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

---

### Post by Installer36 on 2006-02-17
The cd had been used before .All went well withit before .Do they get bad ? I do know that I recently install a new dvd rom but I have also reinstalled XP or Linux several times...Just hit me I have not defraged in between Installs could this be the cause?Or no relation to the problem...Installer36

---

### Post by koma77 on 2006-02-18
Since installing XP works fine I'd like to think that there is no HW error.
And I also tried with different installation CDs with the same result.

I tried to boot with Knoppix live CD and was there able to run parted to partition the drive. 

If I could tell the Ubunutu installet to use the partitions I created in Knoppix without trying to write a new file system I think that I might succeed!

Is there a way to do this?

---

### Post by koma77 on 2006-02-20
Some more info:

If I first install XP on the disk on a partition of 120GB, then try to install Ubuntu in the space left (80GB) the Ubuntu install still fails.

It gets stuck at some percent while creating the file system.

However, when I reboot, I can't boot into XP...

How can the Ubuntu install ruin the XP, even though they should be on different partitions?

---

### Post by br4inwash3r on 2006-02-20
same problem here. just tried installing it last night...both the ubuntu installation and winXP were screwed....the installation halts with some bootstrap...something error message. damn!! now i'm running from the live cd now....

i know, it should've been an easy install. but ALMOST EVERY install guides i found are instructions for a fresh new-computer-empty-unpartitioned-drive installation. WHILE I WAS using an already well and steady winXP. with 3 partition, and one of them is a 5GB FAT32 partition which i saved long ago specifically for linux/ubuntu. and in this case, the one i'm using for ubuntu

well it goes like this. since i don't have room for any more partition. i simply delete this 5GB section and then recreate it from ubuntu partition menu. i did this because before that, the "guided partition" fails, and it sez i have to set it up manually. and i think deleting this partition is the cause of winXP  failure to boot.

but what i dont uderstand is, why does the ubuntu installation also fails?? can anyone help me? and please while ur at it, help me salvage my winXP...

---

