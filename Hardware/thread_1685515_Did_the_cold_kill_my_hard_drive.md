---
title: "Did the cold kill my hard drive?"
date: 2011-02-10
forum: Hardware
---

### Post by M4rotku on 2011-02-10
Hey guys,

I accidentally left my laptop in my car overnight.  It was in it's case, so it was somewhat protected, but not very well.  The temperature got down to 7 degrees F last night and there is a decent chance that there could've been condensation in the car, since I had been running the defrost.

When I turned my computer on, the boot failed and I received the following error:

> [numbers] end_request: I/O error, dev sda, sector 33828183
[numbers] ata 3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[numbers] ata 3.00: irq_stat 0x40000008
[numbers] ata 3.00: failed command: Read FPDMA QUEUED
...
...
[numbers] ata 3.00: status {DRDY ERR}
[numbers] ata 3.00: error: {UNC}

Seeing that it had something to do with the hard drive, I boot from an ubuntu iso image that i had on my hard drive.  The live session is working fine and I used it to run a diagnostics check on my drive.  Before the diagnostics check, the basic disc utility told me that the drive passed the self assessment, but it had 1 bad sector.  I tried running the extended diagnostic test, but it did not finish (it kept getting stuck in the same place, probably the bad sector) and when I canceled the test, the status for the drive switched to "imminent failure".  Since then I tried running the shorter test and they still failed to run all of the way through.  Though, when i canceled the last one, the status of the drive switched back to "passed."

Firstly, is my drive about to fail?  Secondly, if not, then how do I tell ubuntu (and preferably gentoo as well) to work around that bad sector?  Would I have to go into gparted and dissect the partition table so that nothing is over the bad spot?  or is there an easier way?

Much thanks,
M4rotku

---

### Post by steveneddy on 2011-02-10
Leave the laptop in the house where it is warm for a day.

Once it is warmed up a little try to boot it.

Post back.

---

### Post by tgalati4 on 2011-02-11
man badblocks

---

### Post by M4rotku on 2011-02-11
tigalati4, I looked at badblocks, but although it says that it can route info around the bad sector, it wasn't very specific as to how.  Would you be able to help me out with a command or example?

steveneddy, I let it sit for a day and I'm still getting the same results, unfortunately.

---

### Post by M4rotku on 2011-02-12
I thought it might be good to mention that I'm using ext4 for all of my partitions.  I looked at badblocks and it referenced some ext2 filesystem tools, so I'm not sure if that approach would work.

---

### Post by oldfred on 2011-02-12
Have you tried:

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.

sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by M4rotku on 2011-02-13
Update:  I used badblocks and it found a significant amount (around 50) of bad blocks on my hard drive.  I'm assuming that all of these blocks were in the same bad sector, but I don't really understand the difference between the 2 units, so I don't know for sure.  Unfortunately, badblocks didn't fix the problem, since I still receive the same errors when trying to boot the computer (see first post).

I have yet to try oldfred's solution and since it is rather late, I will probably do so tomorrow, though I don't know how that will work differently from badblocks.  Thank you everyone who has helped thus far!

---

### Post by M4rotku on 2011-02-15
bump

---

### Post by JBAlaska on 2011-02-15
Any luck with oldfred's solution?
I doubt it was the cold as I have temporarily fixed many the bad HD by putting it in the freezer overnight and booting it frozen to get the data off, but I guess anythings possible.

---

### Post by M4rotku on 2011-02-15
I saw another thread on this like an hour ago, but it disappeared before I could use its solution and now I can't find it.

That thread was saying that it was a software problem caused by the most recent updates.

---

### Post by M4rotku on 2011-02-15
Here is the other thread, for anyone who is also having this problem:

[http://ubuntuforums.org/showthread.php?t=1034762]("http://ubuntuforums.org/showthread.php?t=1034762")

---

### Post by pricetech on 2011-02-15
For future reference;  The cold probably didn't hurt a thing.  The condensation that gravitated to the cold hard drive, as well as other components probably did.

If it happens again, wrap the laptop, bag and all, in a plastic bag closed tightly and let the temperature equalize before taking it out of the bag.  That should keep any condensation from forming.

Good luck with it.

---

### Post by tgalati4 on 2011-02-15
badblocks is a two step process.  First you run it to find bad blocks--it is a non-destructive test.  If a bunch of blocks show up, then you have have to take the next step:  save the list of bad blocks to a file:

sudo badblocks /dev/sda1 -o my_unusually_long_list_of_bad_blocks.txt

Then you must run fsck with the badblock list to tell the operating system not to use those blocks:

sudo fsck -l my_unusually_long_list_of_bad_blocks.txt /dev/sda1

Of course you can save yourself some time and use the -c switch which runs badblocks and automatically updates the badblock list:

sudo fsck -c /dev/sda1

Try that and see if that fixes your issue.  It could be a cable issue, power issue, drive controller issue.  Did you install smartmontools?

sudo apt-get install smartmontools
sudo smartctl -a

---

### Post by M4rotku on 2011-02-16
Ok, the combination of fsck and the workaround listed in the other thread seems to have worked.  Thanks for your help!

---

