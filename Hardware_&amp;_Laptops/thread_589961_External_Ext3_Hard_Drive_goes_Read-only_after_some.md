---
title: "External Ext3 Hard Drive goes Read-only after some time"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by optimarcus_prime on 2007-10-24
I have a Seagate 250GB external hard drive that worked perfectly in 7.04.  After updating to 7.10, it seems that the hard drive mounts as read/writeable, but after some time it because read-only.  I know it's ext3 because I reformatted it with the command:
```
mke2fs -j -m 0 /dev/sdb1
```
I've also tried to use chown/chmod to fix the problem, but with no luck:
```
marcus:~$ sudo chown -R marcus:marcus /media/disk/
[sudo] password for marcus:
chown: changing ownership of `/media/disk/lost+found': Read-only file system
chown: changing ownership of `/media/disk/.Trash-marcus/test/new file': Read-only file system
chown: changing ownership of `/media/disk/.Trash-marcus/test': Read-only file system
chown: changing ownership of `/media/disk/.Trash-marcus': Read-only file system
chown: changing ownership of `/media/disk/': Read-only file system
```
Any ideas?  I have a sneaking suspicion that fstab/mtab are the culprit, but I can't figure out why, even though I've read up on it.  Please let me know if you need any more info.  Thanks!

---

### Post by optimarcus_prime on 2007-10-25
Bump please?

---

### Post by optimarcus_prime on 2007-10-26
Bump.

---

### Post by Whiffle on 2007-10-26
I ran into this problem the other day with my computer, and never actually solved it.  I have a 500GB Lacie that would go read-only after copying ~11GB of data.  It seems that it detects some kind of fault on the filesystem (supposedly), and makes it read-only to prevent further damage.

However.  I took the drive off my desktop which was having the problem and plugged it into my laptop, and copied all 71 GB of data over the network from my desktop through the laptop and onto the drive w/o a single issue.  

The main difference between the two is that the laptop was running a fresh Gutsy install, and the desktop a Gutsy install that had been upgraded from Feisty or Edgy or whatever.  

I would suggest doing a fresh install of gutsy.

I used a different command though:  mkfs.ext3 /dev/sdc1

---

### Post by 18nikko on 2007-10-26
Hi,
This is due to a 'feature' of the seagate external disks, in that they spin down automatically after 15 minutes. In my post below I have some links to solutions for that problem, now if you can solve mine that would be even better ](*,)

Nicholas

[http://ubuntuforums.org/showthread.php?t=591904](http://ubuntuforums.org/showthread.php?t=591904)

---

### Post by optimarcus_prime on 2007-10-27
> **Whiffle said:**
> I ran into this problem the other day with my computer, and never actually solved it.  I have a 500GB Lacie that would go read-only after copying ~11GB of data.  It seems that it detects some kind of fault on the filesystem (supposedly), and makes it read-only to prevent further damage.

However.  I took the drive off my desktop which was having the problem and plugged it into my laptop, and copied all 71 GB of data over the network from my desktop through the laptop and onto the drive w/o a single issue.  

The main difference between the two is that the laptop was running a fresh Gutsy install, and the desktop a Gutsy install that had been upgraded from Feisty or Edgy or whatever.  

I would suggest doing a fresh install of gutsy.

I used a different command though:  mkfs.ext3 /dev/sdc1
Sorry if I wasn't specific in my information, but this was a fresh install, not an upgrade.

---

### Post by alanhs on 2007-10-29
I am seeing a similar problem on a fresh install of Gutsy on a 500gb USB Segate drive. Reboot clears the problem and there does not seem to be any disk corruption.

---

### Post by optimarcus_prime on 2007-10-30
Interesting.  It seems as though Whiffle's suggestion of formatting using
```
mkfs.ext3 /dev/sdc1
```
worked.  After I reformatted I have been able to use the drive to its full potential for a few days now.  Solved?

---

