---
title: "Hard Drive Failure: A Hoax?"
date: 2011-01-16
forum: Hardware
---

### Post by jacky.alcine on 2011-01-16
I don't know why I didn't come to the forums to begin with. So currently I'm running **e2fsck** in interactive mode because my 320 GB Seagate Expansion Portable Drive S/N (2GH473GA), P/N (9SD2A3-500) has stopped cooperating.

Current S.M.A.R.T Data Status:[INDENT]**Reallocated Sector Count**: Threshold, *36*. Value: [COLOR=Red]**2,076 sectors**[/COLOR].
**Current Pending Sector Count:** Threshold, *0*. Value: **[COLOR=Red]33 sectors[COLOR=Black].[/COLOR][/COLOR]**

[/INDENT]I can't find any warranty information regarding my data, as I've lost the receipt a month and a half ago, and this drive is of fair age (approximately two months old). Currently **e2fsck** is having me answer questions like:
[http://paste.ubuntu.com/554646/](http://paste.ubuntu.com/554646/). Mind you, that's probably an eighth of the output. 

Should I continue with **e2fsck** or is it time to call it quits and throw in the toilet?

**This drive had everything on it, my work, my personal files, configurations, software, *everything***. If there's anyone who's willing to help; please reply as soon as possible.

---

### Post by jacky.alcine on 2011-01-16
**e2fsck** is running with the **-y** flag, so I don't have to keep pushing y.

---

### Post by James78 on 2011-01-16
I'd just say that because you have advance warning of a potential problem, just watch out. Your hard drive may fail tomorrow, it may not fail for 3 more years, but either way, since you know something may be up, I'd suggest you always keep a up to date backup of your most important stuff (e.g. configurations, list of software installed, maybe your home folder, movies, music ..). Two months old.. I have to admit that's pretty quick for something like this to be happening to a drive.

If it helps, I have a drive that's similar to that. It's still running great, but I'm not holding data on it without backing it up. It's in a RAID. If the drive goes, I still have my data. ;)

---

### Post by jacky.alcine on 2011-01-16
Will do, James78. I think after (God forbid) this dies, I'll invest in a dedicated server just for my backups.

---

### Post by IcarusR on 2011-01-16
If you need to RMA it you used to be able to go to seagate website & do it by serial number.

Yet another example of how blasé people have become when backups are concerned !!

---

### Post by gradinaruvasile on 2011-01-16
Watch out for errors like that. I have 2 drives with errors on them and if the os wants to read the affected zone, it freezes the computer (plugging them out/in from theit sata connectors regains control). But if you happen to have bad sectors in the first part of the partition, it may become unmountable.

---

### Post by efflandt on 2011-01-16
See what seagate.com has for Seatools, if they have a version that can boot from CD if you do not still have Windows.

When I had bad sector problems with a WD laptop drive, they could tell it was under warranty from manufacture date of that serial number, so I did not have to dig up the receipt.  Not sure how gentle my boss' grandsons were with it.

---

### Post by knedle on 2011-01-16
Hello,
you may try to use [DD Rescue]("http://wiki.linuxquestions.org/wiki/Dd_rescue"), which is pretty nice program, that helped me few times. You will probably not be able to get all your data back (I'm pretty sure you should get back something about 90% of your data), but 90% is much better than 0%.

First you will need another drive, go to shop and get one. If I were you I would buy anything cheap, as long as it is not Seagate*.

Then you will have to create partitions with the same size (or slightly bigger) that you have on your broken drive. Reason for this is you will be copying everything from your damaged drive to new one (so not only data, but also free space). Now if your source partition is 100,1GB and your destination partition happens to be 100,0999GB data will not fit, but if you create partition with size od 100,2GB, you will waste a little of free space, but it will fit for sure. For creating partitions you can use whatever you are comfortable with, it may be fdisk, gparted or anything else. Partitions doesn't have to be in the same order as on source drive.

Third step is to execute ```
dd_rescue /dev/sdb1 /dev/sdc1
``` where /dev/sdb1 is your source partition, /dev/sdc1 is destionation.

Now you have your partition copied to your new drive (if you have more partitions remember to copy them all). You can go to seagate.com, send them your HDD (you don't need any invoice for that, just a serial number that should be written on your drive), and once they give you new one, you can ebay it. ;)

* Yeah, I know that any HDD can be broken and it may be Seagate, Samsung, WD, or anything else. But in past years I had to deal with a lot of broken dives and majority of them were Seagates, when my company switched to Samsungs and WDs our problems with HDDs become less frequent. So just make yourself a favor and don't use Seagate drives if you like your files.

---

### Post by jacky.alcine on 2011-01-16
[B]Thank you everyone for replying so swiftly!

[/B]Seagate does have software that *attempts* to repair, but it doesn't do anything. It's practically a **chkdsk** on Windows. 

But I am making progress. Using deductive reasoning, I found the area on the drive where the issue being caused. **Would the following command**:

```
sudo dd if=/dev/zero of=/dev/sdb9 bs=4k
```

**do anything for me?**

---

### Post by CharlesA on 2011-01-16
That will just overwrite the drive with zeros.

If you run the seagate utility, it should be able to see if there are problems on the drive, so you can RMA it.

---

### Post by CharlesA on 2011-01-16
That will just overwrite the drive with zeros.

If you run the seagate utility, it should be able to see if there are problems on the drive, so you can RMA it.

---

### Post by IcarusR on 2011-01-16
Before you do much on it I would recommend you image it to another drive first. 
Then if you accidentaly run a command like the one you posted that fills it with zeros you still have the image to work on.
You can use something like clonzilla.

[http://clonezilla.org/]("http://clonezilla.org/")

---

### Post by 1clue on 2011-01-16
You don't need or even particularly want a separate server for backups.  It's just one more piece of hardware to have go bad on you.

The best thing you can do to prevent this in the future is to have regular backups.  You don't need special software or anything else, it can be really simple.

Get a removable drive which is as large as you think practical.  Last I checked 1 TB cost less than $100 USD.

Plug it in, make some folders.  I name mine with a date like '2011-01-16-myhost'

Inside that, I throw /etc, /home, and anything else containing configuration or data that I think is important.  If you have a collection of huge files like music or movies, then make a second partition for that and format with a large file friendly format.  Things like databases need to be backed up into an archive and then transferred or you'll have a useless file when you get done.

I use a command line, **cp -prd /home/me /backup/2011-01-16-myhost/home/me**


DO NOT make a backup of your whole drive.  Similarly avoid huge tar files or zips of any sort, if the file gets corrupted you lost your entire backup.

If two years from now you need to restore you will want the latest Ubuntu anyway, and by next week some software update will come out that makes your entire disk backup obsolete.  You're not backing up your operating system, you can get that again in a few minutes any time you want it.

Most importantly, when you get done with your backup unplug the drive entirely and move it away from your computer.  Preferably another room, in case you house gets robbed you have your data.  Or if you're really paranoid you can take it to some other building so if your house burns down you still have your data.

Chances are you'll get a bunch of backups on there.  When the drive gets full, you remove the oldest or have some scheme for keeping every third one, or whatever works for you.

Good luck.  Unfortunately the time to plan for backups is before you need them.  After literally decades of messing with them I have my own methods, and they are as simple as I can possibly make them.  I've spent years writing backups to tape, only to figure out that the tapes weren't reliable enough.  Then DVD, they're not big enough and not reliable enough either.  I've tried software on a schedule, but that is often proprietary or fragile.  Nothing beats remembering to back up every Sunday for example, and then pulling the drive back out.

---

### Post by CharlesA on 2011-01-16
To add to 1clue: I bought a 3TB drive for just under $200 USD (it was on sale). I've seen 2TB drives going for 159 and 1TB drives around about 100.

I have an rsync script run daily, so if my server goes down, I'll lose at most 1 day of data.

---

### Post by psusi on 2011-01-16
Your subject reads "A Hoax?", which makes no sense.

---

### Post by jacky.alcine on 2011-01-16
> **CharlesA said:**
> That will just overwrite the drive with zeros.

If you run the seagate utility, it should be able to see if there are problems on the drive, so you can RMA it.
 
I did that, and it failed this Long Generic test.
I'm shipping it to Seagate in a few days. =/

---

### Post by jacky.alcine on 2011-01-16
> **psusi said:**
> Your subject reads "A Hoax?", which makes no sense.

I wasn't sure if it was really not working because if I wrote to a partition that wasn't full, it worked. And retrieval happened as well.

---

