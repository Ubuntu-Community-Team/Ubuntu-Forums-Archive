---
title: "two hard drives"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by broth420 on 2007-09-09
Just a question.  I have a WD 120GB SATA drive and a WD 500Gb SATA drive in the same machine.  Can I set the swap parition (2GB), / parition (90GB), and /var partition (whatever's left) on the 120GB drive, and then put /home on the 500GB drive?  Is there a better way?  If so, what are your suggestions?

---

### Post by kidders on 2007-09-10
Hi there,

It's hard to offer you intelligent suggestions on this one, because what the best choices are (and how much of a difference your choices make) are unique to you.

In hardware terms, one of your disks may be faster than the other, or have a bigger cache perhaps ... things that would make them perform differently. Additionally, you've left us guessing as to how you use your box. Judging by the amount of swap you need, you might either have very little RAM, or do a lot of heavy multimedia work. In either case, swap performance would be an issue worth considering.

Some general observations:[LIST]
[*]Mostly, people in your position will like to try to make as much use as possible of both physical devices, essentially aiming to have each working equally hard all the time.
[*]For some users, that might involve doing things like putting one or more swap partitions on each disk.
[*]Don't feel like you *have* to allocate all of the available space right now. As your use of your computer evolves, you may encounter new requirements you can't anticipate today.
[*]You may want to "waste" some disk space, and introduce some redundancy into your system. For instance, if you were content to throw away 120GiB of the larger drive, you could mirror the entire smaller one, for greater reliability or read performance.
[*]Easy recoverability is another concern. Imagine you were forced to reinstall your OS tomorrow. What filesystem configuration would make the job as easy as humanly possible? A web developer might want /var on its own filesystem (or even on a disk by itself).
[*]In terms of day-to-day usage, gamers may want their /opt or /usr/local to be hot-swappable between multiple PCs; software developers might want /usr/src on a separate physical device than the rest of their system, so building software doesn't cripple its response time.....
[*]Then, there are more common-sensical issues to consider, like the fact that some computers will very often want to link & swap at the same time. So, given the choice, it's at least theoretically sensible not to put /usr/lib on the same physical device as your top priority swap file/partition.[/LIST]I hope that's of some help. The short answer is that you can do anything you like, really ... Linux isn't fussy. What to do all comes down to how you want your computer to work.

---

### Post by broth420 on 2007-09-11
thanks for the detailed answer.  I for some reason did run into issues when attempting to put /home on the drive.  In manual mode, it kept not creating a partition of the full size of the drive?  I would tell it to use the entire disk, and then it would scan the drive and the parition would be 71GB (could it have had something to do with the fact the drive was an old NTFS drive?).  I was confused.  What I ended up doing was just leaving it out and then formatting the drive once the system was up.  It created a mount point and that was working pretty well (although I had to mnt the drive manually, cause I was in a hurry and didn't feel like adding it into the fstab settings).  Unfortunately, I really wanted to do a proof of concept, so I rebuilt the system again.  This time, I just choose to format the drive (using the parititon system above) and it locked up the install during the format.  I turned the system off, and tried again, but it did the same thing.  Started over again, left the drive alone.  The system flew through the install no problems.  But the drive was just a mnt point.  How can I get that second drive to contain just the /home parition?

---

### Post by eentonig on 2007-09-11
I see no reason why. This is my partition table:

400G HDrive 1:
/dev/sda1             9.7G  273M  8.9G   3% /
/dev/sda2             241G  139G   90G  61% /home
/dev/sda3             9.7G  151M  9.0G   2% /media/sda3    (unused partion for Ubuntu +1 transition)
/dev/sda5             9.7G  151M  9.0G   2% /media/sda5  (unused partion for other OS installs)
/dev/sda6              49G  3.3G   43G   8% /usr
/dev/sda7              47G   15G   29G  35% /var

400G HD2:
/dev/sdb1             367G  185G  164G  53% /media/disk  (Backup drive. Contains mostly copies from /etc, ~/ and /var/www)

---

### Post by kidders on 2007-09-11
> **broth420 said:**
> In manual mode, it kept not creating a partition of the full size of the drive?I presume you're referring to the Ubuntu installer there. Personally, I almost never use OS installers to partition my disks, and tend to try to avoid letting them create filesystems, where possible. Aside from giving me far better control over what I end up with, it eliminates any messing about I might have to do to get around installer bugs.

A lot of people seem to encounter odd problems using Ubuntu's installer to configure their partitions & filesystems, so I would suggest not using it.

> **broth420 said:**
> How can I get that second drive to contain just the /home parition?Reinstalling Linux is never necessary to do something like that. There's plenty of help here (and on other sites) on the subject. All you really need to do is create a new filesystem, move your /home into it, and mount it. If you feel in any way unsure, it's always safest to boot from a CD or something first though.

---

### Post by broth420 on 2007-09-11
thanks for your help.  What do you use to partition your drive?  and then how does that integrate into the install?

---

### Post by dabl on 2007-09-11
Download the ISO and make yourself a GParted Live CD, to use for hard drive partitioning tasks.  Get it here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

:)

---

### Post by kidders on 2007-09-11
> **broth420 said:**
> What do you use to partition your drive?Personally, I've used cfdisk religiously for years ... for DOS partition tables anyway. I've never even *heard* of someone having a problem with it, and it's a little less unfriendly than fdisk. Dabl's suggestion is perfectly good though, if you'd prefer to use gparted, a utility than can also create filesystems.

> **broth420 said:**
> how does that integrate into the install?I don't really know what you mean by that. :-(

---

### Post by broth420 on 2007-09-12
> **kidders said:**
> Personally, I've used cfdisk religiously for years ... for DOS partition tables anyway. I've never even *heard* of someone having a problem with it, and it's a little less unfriendly than fdisk. Dabl's suggestion is perfectly good though, if you'd prefer to use gparted, a utility than can also create filesystems.

I don't really know what you mean by that. :-(

What I meant was, where did it fit into the installation process.  
I actually tried it last night, and just used Gparted to create the partitions, and then installed Ubuntu using those partitions I created earlier.
Thanks everyone.

---

### Post by kidders on 2007-09-12
Hey again,

> **broth420 said:**
> What I meant was, where did it fit into the installation process.Ahh... sorry. Well, as I'm sure you know by now anyway, it doesn't. There's no reason not to pre-partition your hard disks before you even *start* a Linux installation. On the contrary, many people prefer to do so, because they get to use partitioners they're already familiar with.

Glad you've sorted everything out. :-)

---

