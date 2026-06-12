---
title: "Recovering from a failed external hard drive"
date: 2014-11-16
forum: Hardware
---

### Post by Djvoldi123 on 2014-11-16
My Fantom HD external hard drive(1 TB) stopped working properly about six months ago. During its decline, it started getting more and more bad sectors, until its final crash some weeks back. Before the crash, most of the files in the drive could be loaded, but only on Ubuntu - when I plugged the drive into a Windows XP computer, a message box popped up saying "Format new drive". In Ubuntu, every time the drive mounted, a message box would come up saying "Hard drive failure imminent" or something like that, so I started backing up the files in the drive. However, I wasn't fast enough. Soon, the drive stopped working completely.
Now, whenever I plug the drive into an Ubuntu computer, the same error pops up, but I am unable to mount and view the drive in either the file manager or the Ubuntu sidebar. I *can* see it on Disk Utility, though.
Is there any way to recover the files on the drive? I can't really send the drive to an expert because I live in the countryside.

---

### Post by Mark Phelps on 2014-11-17
> Now, whenever I plug the drive into an Ubuntu computer, the same error pops up,WHICH error -- the format message, or the hard drive failure imminent message?

Sorry, but no OS is going to help you if the hard drive physically fails.

As to sending the drive our for recovery, I had to contact a local recovery service recently because a hard drive from my server failed, and they wanted $1000 USD to "repair" it, which I later found out, is a typical "fee".  So, unless you're prepared to pay that kind of money, don't plan on using a professional drive recovery service.

---

### Post by jcm2302-a on 2014-11-25
There is a possible solution 

wether or not the hard drive has bad sectors or not if it still physically spins it is likely it wont mount but the information contained is theroretically accessable in ubuntu install testdisk 

sudo apt-get install testdisk

use the utility to backup the drive on your internal drive and either get a new external or reformat the old drive replace files and continue the madness 

always back out of stand alone media players XBox DVD TV etc. to the main menue before removing media and unmount media from Ubuntu or Windows it is likely the difrent OS caused the errors or the case around the drive is cheap and faulty so if a good internal drive is possible it is the best bet or if media is transfered alot set up file server or get multiple drives and update them not so often and always on same OS 

hope this helps just a thought

---

### Post by Reha_Andrew on 2014-11-27
Find you PCB matching from other drive with similar stats and then swap both.   It will help to prevent your data.Find you pcb matching from other drive with similar stats and then swap both.   It will help to prevent your data.

---

