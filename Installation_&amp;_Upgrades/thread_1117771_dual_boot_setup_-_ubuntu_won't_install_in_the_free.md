---
title: "dual boot setup - ubuntu won't install in the freed space"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by jome on 2009-04-06
Hello,

I have just purchased a new Sony laptop with Vista installed. I want to have a dual boot with Ubuntu as I had on my old laptop. I found a manual on [apcmag]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") how to do this. I get stuck on page 3 in the disk partitioner. It says: 

> Choose "Manual - use the largest continuous free space". This will automatically select the unpartitioned space we created earlier using the Shrink tool.

But when I select that option the whole disk gets selected. How do I make sure that Vista and the recovery partition are not overwritten?

---

### Post by zvacet on 2009-04-07
You should see options like [this]("http://psychocats.s465.sureserver.com/ubuntu/dualboot").If you choose manual you will have opportunity to make separate home partition and I will recommend that.

---

### Post by dandnsmith on 2009-04-07
After fairly recent experiences installing (and failing) ubuntu 8.10, I'd go for the manual method (with care).
One thing I found to give trouble was to start using one method, then backtrack and start another - I didn't get a good result until I started the install, picked the method for space allocation, and then carried it through.

---

### Post by Zireth ZH on 2009-04-07
I recommend you to select your drives manually... linux's partition should go as "ext3" .. u also need a "swap" partition ..  I chose an 8 mb free space partition for swap... Im new with ubuntu, and thats how it worked for me.. Hope this works for you too.):P

---

### Post by jome on 2009-04-08
I checked and manually seems to be the right choice.
Now I need to know exactly what kind and how big the partitions I create should be.

I have a 320GB disk with 2 partitions:
/dev/sda1    7970 MB (6694 MB used)
/dev/sda2  169459 MB (35556 MB used)
free space 142639 MB

Vista is located in sda2 and I think sda1 is a recovery partition.

I think I will be using Ubuntu and Vista equally often.

---

### Post by SnickerSnack on 2009-04-08
I tried a similar thing yesterday.  I had to resize the windows partition from ~292 gb down to ~90 gb.  Then I made an extended partition with several logical partitions in it.  Most of them were for linux, but I also made a 120 gb Fat32 logical partition to use as shared storage.

When I later rebooted into windows, windows couldn't run because some files were missing or damaged.  That doesn't usually happen, but it can.  So, I'd recommend not using linux to resize the windows partition unless you're prepared to reinstall windows (ie make a backup first).

---

### Post by uidb4056 on 2009-04-08
> **jome said:**
> I checked and manually seems to be the right choice.
Now I need to know exactly what kind and how big the partitions I create should be.

I have a 320GB disk with 2 partitions:
/dev/sda1    7970 MB (6694 MB used)
/dev/sda2  169459 MB (35556 MB used)
free space 142639 MB

Vista is located in sda2 and I think sda1 is a recovery partition.

I think I will be using Ubuntu and Vista equally often.

Then going to manual diskspace configuration, I would recommend that you create the needed partitions not as primary partition but as logical partitions because there is a limit of maximum number of primary partitions of 4, this way you can choose if you want a separate partition for /home in addition to / and swap or later you may want to install another distro or Ubuntu release for testing pourposes, otherwise you will need in this cases delete one of the 4 primary partitions to be able to create logical ones.

---

### Post by Mark Phelps on 2009-04-08
> **SnickerSnack said:**
> When I later rebooted into windows, windows couldn't run because some files were missing or damaged.  That doesn't usually happen, but it can.  So, I'd recommend not using linux to resize the windows partition unless you're prepared to reinstall windows (ie make a backup first).

Well ... I've been trying to warn folks for months NOT to do exactly what you did -- because of what happened to you (and others) as a result.  But, I guess I'm the ONLY person who reads the warning information in GParted about resizing Vista partitions.

BTW, you don't have to reinstall Vista.  If you can lay your hands on a Vista DVD (or you can torrent a recovery CD image from the NeoSmart forums), you can boot into it, run Startup Repair, and you'll probably be OK again. A lot less work than reinstalling from scratch.

---

### Post by jome on 2009-04-09
@SnickerSnack: That is why I followed the manual I posted and first shrank the Vista partition from inside Vista using the disk manager.

---

### Post by Mark Phelps on 2009-04-09
Bet it didn't shrink much, did it?  

I guess I should be surprised about how poor that tool is, but my previous experiences with MS products bundling features has shown this to be all too typical.

Unfortunately, they've done something with the Vista OS partition and the Vista boot loader that is proving difficult for others to figure out sufficiently that they can reliably shrink Vista partitions without the danger of corruption.

It wouldn't be like MS to hide information from us so that we are forced to use their products, now would it.

---

### Post by meierfra. on 2009-04-09
[QUOTE=SnickerSnack]When I later rebooted into windows, windows couldn't run because some files were missing or damaged. That doesn't usually happen, but it can. So, I'd recommend not using linux to resize the windows partition unless you're prepared to reinstall windows (ie make a backup first).[/QUOTE]

SnickerSnack: I looked at your thread and I'm not sure that your boot problem was caused by resizing.  The most common causes for Vista failing to boot after an Ubuntu Installation are

[LIST=1]
[*]Grub is configured wrongly.
[*]The partition containing the Vista boot files was deleted or formated.
[*]Problems caused by resizing the Vista partition.

[/LIST]

Number 3 is the least common one of these three.
To you remember the error message you got?  Was it "bootmgr is missing", "ntldr" is missing"  or did you get a BSOD with "winload.exe missing"?

Anyway, all three of these problems can be fixed  with a little bit of work and do not require reinstalling Vista. 

Cases where Vista needs to reinstalled are extremely rare and are almost always caused by the user.

---

### Post by jome on 2009-04-14
It worked. I had to repartition after because Ubuntu created 3 partitions out of the logical partition I created for it. Now there is 4MB of space between the windows and linux partitions.

Now for my next problem: I can´t read the ext3 partition from Windows. I can read it on my old laptop. It has a driveletter D assigned to it.

---

