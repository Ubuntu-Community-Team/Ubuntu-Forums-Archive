---
title: "how to install Ubuntu 8.10 in external USB hard drive?"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by acton on 2009-02-26
How do I install Ubuntu 8.10 on an external USB hard drive that is already partitioned? 

I boot Dell laptop with Ubuntu 8.10 live CD mode successfully. Then, I run 'install' program from Ubuntu desktop by clicking the 'install' icon. However, on the 'install' step 4 of 7, the 'install' program ask me to choose partition options from internal hard drive on /dev/sda (all options are sda1, sda2,...,sda4), and no external USB hard drive partition options (no option is from /dev/sdb). So, how can I install Ubuntu 8.10 into external USB hard drive?

Ubuntu seems to recognize the USB external Hard drive, and Ubuntu automatically mount the plugged USB hard drive successfully. BUT Ubuntu does not want to install external USB hard drive. When I run Ubuntu installer, on step 4 of 7, installer has only internal hard drive options (e.g. dev/sda1, ...,sda5), and no external USB hard drive options (no /dev/sdb1,...,/sdb5). 

[update: I found that unmount external USB hard drive first, then run the installer again. Now the installer can recognizes the external disk and can install Ubuntu.  But there is 2 new problems: 1) how can I recognize which external partition is my target when I already unmount all external USB drive partitions. e.g. how can I check /dev/sdb5 (one of 4 external USB partitions) contents and free space? 2) how to avoid Ubuntu boot loader mess up internal hard drive MBR?]

The external USB hard drive is Maxtor 40 GB Ultra ATA/100 hard drive, and it has a NexStarr-3 external 3.5" USB hard drive enclosure with USB 2.0 interface. It was already partitioned in 4 partitions, and each partition has 10 GB capacity (all NTFS format). The USB hard drive is connected to a Dell Inspiron 6400 laptop's standard USB port, and laptop BIOS can be set up to be the startup from external USB hard drive. 

The internal hard drive already has Dell pre-installed WinXP, media Direct partition, and ghost image recovery partition, so I did not want install Ubuntu into internal drive. I also do not want install Ubuntu into USB pen drive, or USB flash drive because I already have them. 

The 40 GB external USB hard drive already has WinXP installed and has 4 NTFS formatted partitions. Each partition has 10 GB capacity. 3 partitions has full of data already. Only one of 4 partition has 10 GB free space for installing Ubuntu.

Thank you in advance,

---

### Post by ScarySquirrel on 2009-02-26
Going the external hard drive route, eh?  I had to do that when my internal drive failed.  Portability is a beautiful thing.  Anyway, I just have a few questions, which follow, in order of importance:

1.  What is the model of the hard drive portion of the external hard drive?

2.  Does the hard drive connect to the USB part of the external hard drive by means of SATA or IDE?  (SATA stands for Secure Advanced Technology Attachment, and IDE, the older format, stands for Integrated Drive Electronics)

3.  What is the model of External Hard Drive Case that you have?

4.  Does it connect by means of USB 1.1 or something like that, or does it have USB 2.0 or higher?

5.  Why not put the model of your computer and external hard drive in the signature?

Anyway, I wish you the best of luck until you get back to me,

[SIZE="3"][FONT="Georgia"]ScarySquirrel[/FONT][/SIZE]

---

### Post by acton on 2009-02-26
Hi, ScarySquirrel,

Thank you for your quick reply. Here is my answers.

1. Hard Drive Model: Maxtor 40 GB Ultra ATA/100 hard drive, 5400RPM
2. Standard USB port at Dell laptop Inspiron 6400.
3. NexStar-3 External 3.5 Hard Drive Enclosure, with USB 2.0 Interface.
4. USB 2.0 
5. Title of post is too long to post here if I add "Dell Inspiron 6400" laptop model, and "NexStar-3 External 3.5 Hard Drive Enclosure, with USB 2.0 Interface" USB case model name.

Ubuntu seems to recognize the USB external Hard drive, BUT it does not want to install there. It worked in the past (at least from version 7.10), so I don't know if this can be considered as a bug ...

Thank you,

---

### Post by ScarySquirrel on 2009-02-28
I will make at least ten solutions proposals before I give up.  In four months nobody has helped me out with my problem yet, which you can see in my signature, and I do not want anyone else to have to deal with that.:mad:

1.  The first thing I would have suggested was that you try unmounting the disks, so you're already one step ahead of me.:KS

2.  To make sure that you know which partition is which, I have the following hack fix for you:  use the "resizer" to make the parts on the target drive a slightly different size from one another, even if it's only by a few hundred or even just a few megabytes.  The experts will probably tell you something about editing the fstab, but I am not confident enough about that to give any advice, in other words, I'm a newb.  Anyway, it worked for me with my external hard drive.  Do not worry too much about the warning that comes with the resizer.  Any partition editing runs some risk of corrupting data, but it has never done this to me, and I've pulled some crazy stuff.  :P

3.  The Ubuntu installer is a subtle, stealthy beast.  It can sneakily install into its prey while still leaving the MBR intact, and leaving its mortal enemy, Windows with no trace of its existence other than an unavailable partition.  Clarify your question about the MBR further.  

4.  Remember that you will have to format the target partition as the filesystem "et3".

5.  By the way, it's the rare person who can even get as far as you have so far, so, uh, kudos.:KS

It seems like we come closer to a final solution,

[FONT="Franklin Gothic Medium"][SIZE="4"]ScarySquirrel[/SIZE][/FONT]

---

