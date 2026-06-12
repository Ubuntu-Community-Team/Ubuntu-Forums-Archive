---
title: "Best storage practices?"
date: 2015-09-06
forum: Hardware
---

### Post by pepsifx357 on 2015-09-06
Hi everyone, I thought I'd take a moment to start a discussion on storage practices in linux and what everyone is doing in this regard.  I try to learn something new everyday and upon yet another drive failure, I thought this subject would be something I should do more research on and get some feedback.

I was wanting to know what everyone else was doing about their storage?  I'm not new to the linux world, so I know about raid, lvm, btrfs, zfs, ect.  I'm also learning about how "Enterprise" class hard drives differ from these $70 garbage drives I keep buying.  However, I started getting into SAS drives and I would need a controller.  They're not cheap either, but would it be worth it?  I'm also curious as to how everyone partitions their drives, what kind of raid schemes and lvm setups you have.  If you've got a FreeNAS system setup, serving your computer, I'd like to hear about it.

My latest setup were three 500GB seagate hard drives in an LVM with a separate [root(EXT4)/home(BTRFS)/swap] logical volumes, and a 500MB XFS boot partition on /dev/sda1.  The other day, I had an I/O error on one of the drives.  I was able to run FSCK and get it up and running enough to save my stuff, but I feel that if I had setup my disks using a raid 5 scheme I might has saved my self some trouble.  Most of my critical stuff lives in the cloud, so no problems there.  Thoughts?

Also, in the interest of speeding up my computer in general and adding a small SSD drive to the mix, which folders would be a good candidate for an SSD, such as swap, /var, /srv, /tmp ect.  A folder that gets written to a lot and could use the speed of an SSD.  I've got a 40GB intel SSD that I'm not using at the moment, which is why I'm asking.

I really want a better storage plan than the one I've got.  Think you guys could help me out?

---

### Post by weatherman2 on 2015-09-06
I'd put everything in the OS on the SSD - /var /usr /etc - everything except perhaps /home (if you store data there - some of us don't).  For me, 40GB is more than adequate for an installation of Ubuntu.  I'd put my swap there, too.

I don't bother with RAID anymore, because my data isn't changing constantly.  RAID only protects against hard drive failure, not file system corruption, power spike (not every surge protector can handle every power surge), accidental deletion, or (if your data is exposed to a Windows machine) malicious corruption by malware.  For someone with a mission-critical server where data is constantly being changed - for example a SQL server that keeps customer orders or something - then a RAID would be essential.  In many cases it is not but adds extra expense and complexity.

Instead, I expect my hard drives to fail at some point, and I use redundancy: I keep my data on multiple devices that are not always online.  If I setup a new data archive, I'll buy three identical hard drives: one for the server and two that sync the original hard drive when needed.  The third drive is a copy of the other two but kept in another physical location and swapped with the other one occasionally.  The downside of this scheme of course is that my backup can get stale, but for any data that really changes that often I do other backups over a local network automatically.

I use LVM for my operating system only, mostly so it's easy to make a backup via snapshot while the OS is booted.  I use ext4 for almost everything.  I use rsync, rdiff-backup, and sometimes even the ancient dump command to make backups.

---

### Post by weatherman2 on 2015-09-06
I also monitor S.M.A.R.T. on all my drives.  I have a script that monitors changes in S.M.A.R.T. Attributes and emails me if there's a change.  For example, if suddenly there's a pending sector or a reallocated sector that wasn't there yesterday, I take notice.  You can't always rely on S.M.A.R.T. to notify you before a drive fails, but it has given me early warning numerous times of a drive problem.

---

### Post by jason_gibson2 on 2015-09-06
I don't do much with special partitions or lvm since I'm on a laptop and only have room for the 1 drive (120gb ssd). Every night I mirror my /data partition to my server though. Is one backup. Once I move into my new place I will also be adding a Western Digital MyCloud device to the router for an additional backup. I keep the truly irreplaceable things synced to my google drive though. Of course this all is based on me not having a ton of data to worry about to begin with. I'm sure if I was dealing with hundreds of gbs / multiple tbs my strategy would be different.

Things to do - Switch to a versioned backup system if possible.

---

### Post by weatherman2 on 2015-09-06
You can do versioned backup with rsync, the way Apple does Time Machine, using hard links:

[https://blog.interlinked.org/tutorials/rsync_time_machine.html?hc_location=ufi](https://blog.interlinked.org/tutorials/rsync_time_machine.html?hc_location=ufi)

---

### Post by brian-mccumber on 2015-09-07
I use external hdd's and back my files up manually or by script at different intervals when I figure enough of them have changed to warrant it. I probably back up more when I am making a website or app for someone and usually there is a copy of that on a web server too so my client can watch it grow. I will never use a cloud based storage or backup, ever. I am not going to pay a fee for accessing my own files when I can go out and buy a 1tb hdd for next to nothing and the thought of other people having access to me and my clients data does not appeal to me at all. Privacy concerns are one of the main reasons I just switched from Windows anyway due to researching Windows 10 extensively and watching each release of their OS take more and more control away from the computer's owner. I am not putting that crap on my computers anymore. I don't feel I need to rely on MS or Apple or any other big company to take care of my data or control my computer for me, I can do it myself. And I don't need other's digging through my data so they can serve me ads for crap I will never buy anyway. I am under the impression that personal computer is personal and I don't need a company running mine. I don't run a server or anything tho unless you count a dev lamp server as a server, I don't serve web pages to public I only use it when I am using php/mysql for a client's project. I just have a laptop and a desktop and alot of my files are duplicated between the two machines anyway. But my computers are pretty much networked together so if I need something from one I can get it with the other fairly easily. I only back up my personal files not the whole OS, I can always reinstall the OS so I don't count it as a priority. And when I installed Ubuntu on my computers I partitioned my drive in three parts, /, /home, and swap so if something happens to the OS I can just reinstall that drive and not loose any data on the other. Even if I was running a web server that used and stored sensitive user data I still would not use cloud storage for anything, I would set up a raid. Sorry about the rant but really, how much control over a computer does the OS manufacturer need? This is my machine not Microsoft's. I bought this thing, not them. According to Microsoft all users are dumb cows and they can't be trusted with their own machines and this upset me to the point where I will never use MS OS again and I had been using MS OS's since DOS.

---

### Post by Yellow Pasque on 2015-09-07
>  I'd put my swap (on the SSD), too.

I guess the amount of SSD writes isn't as important as it used to be with SSD's having increased life expectancy, but I wouldn't put swap (or /var) on the SSD, unless I was on a system with limited RAM (whether physically limited or relatively limited to the tasks I do) and swap performance was important. Even then, I would turn down "swappiness" to 10 or less to avoid unnecessary writes to the SSD.

> RAID only protects against hard drive failure
True, but depending on your usage habits, that may be the most risky cause by far. I have my media stored on a RAID 1 mirror, because I'm really good at procrastinating backups to my external drive and before I know it, it's been months or almost a year since I've bothered.

---

### Post by pepsifx357 on 2015-09-07
> **weatherman2 said:**
> I also monitor S.M.A.R.T. on all my drives.  I have a script that monitors changes in S.M.A.R.T. Attributes and emails me if there's a change.  For example, if suddenly there's a pending sector or a reallocated sector that wasn't there yesterday, I take notice.  You can't always rely on S.M.A.R.T. to notify you before a drive fails, but it has given me early warning numerous times of a drive problem.

I need to know how to do this.

---

### Post by weatherman2 on 2015-09-07
> **Temüjin said:**
> I guess the amount of SSD writes isn't as important as it used to be with SSD's having increased life expectancy, but I wouldn't put swap (or /var) on the SSD,

That is my belief, from what I have read: SSDs have much greater life expectancy.  I recently replaced an Intel consumer SSD that had been in a web/email server where the SSD had been running 24/7 for three years (with swap and /var on it).  I replaced it only because I felt I should - it was working fine, and according to S.M.A.R.T. the media was not about to wear out or anything.  Plus no partition was nearly 100% utilized; SSD firmware is intelligent enough to distribute writes around to different flash cells, so that even though you may be writing the same file (or swap partition) over and over again, you aren't necessarily re-writing the same flash cells over and over again.  Now, if your drive was running near capacity, then that would be different - you'd be potentially writing to the same cells more often.

In this server, there was no physical hard drive.  Including one just because I was worried about the SSD wearing out added complexity, power consumption, etc.  It seemed pointless.  And the cost of SSDs has fallen so low that I'd argue it's not productive to treat them like gold anymore.  Treat it like a tire that will eventually wear out - but replace it before it does and you'll be fine.  Of course, regular backups are essential.

> True, but depending on your usage habits, that may be the most risky cause by far. I have my media stored on a RAID 1 mirror, because I'm really good at procrastinating backups to my external drive and before I know it, it's been months or almost a year since I've bothered.

And that's one big failing of a RAID: it makes you lazier.  You worry less about the other dangers to your data because you feel overconfident about your RAID protecting you.  But I've experienced those examples I gave above - malware corruption of data, file system corruption, and power spikes - that destroyed data; though I was not using a RAID in any of them, it would have been useless,  Once you learn to make regular backups, routinely (or setup an automatic backup), you don't have to rely on your RAID as much.

---

### Post by Yellow Pasque on 2015-09-07
> **weatherman2 said:**
> And that's one big failing of a RAID: it makes you lazier.

I think there are plenty of people using RAID that realize it's not a substitute for backups. Like I said, I always procrastinated when it came to backups. I agree that it doesn't make sense for everyone, but if you have the available disks/space and hard disk failure is your biggest concern, it makes sense.

---

### Post by weatherman2 on 2015-09-07
Well, my biggest concern is data loss, from all causes, not just one.  Is data loss from hard drive failure 2X more likely than from other causes?  10X more likely?  Who knows?  It depends on your situation, how you monitor the drives, how often your data changes, etc.  And you yourself implied that your RAID reduces your worry about procrastinating in making your backups.  To me, that means you are increasing your risk of data loss from other causes.

---

### Post by Yellow Pasque on 2015-09-07
> To me, that means you are increasing your risk of data loss from other causes.

Only if you change your backup behavior. Like I said, my backup behavior was less than ideal even **before** I moved to RAID...
If you're trying to convince me that RAID is useless or counter-productive for my scenario, you're wasting your time.

---

### Post by weatherman2 on 2015-09-07
I've already said that RAID is essential in some situations.  I don't know what your "scenario" is - maybe it is essential for you.  However, I have seen too many people (not you) seem to get carried away with a RAID they probably didn't need, without much consideration to their backup plan or to the other very real threats to their data.  RAID is certainly not a substitute for robust backup practices.

---

### Post by lukeiamyourfather on 2015-09-09
> **pepsifx357 said:**
> I'm also learning about how "Enterprise" class hard drives differ from these $70 garbage drives I keep buying.  However, I started getting into SAS drives and I would need a controller.  They're not cheap either, but would it be worth it?

For most home users SAS drives are not worth it. They offer features usually only meaningful in mission critical situations like the ability to have redundant disk controllers. There are a few other handy features like longer cable runs (higher voltage signal) to external JBOD enclosures but again for most home users this is a moot point. For what it's worth I've setup several file servers that have amounted to hundreds of SATA drives in use 24/7 for several years and there have been no issues.

> **pepsifx357 said:**
> I really want a better storage plan than the one I've got.  Think you guys could help me out?

I've found that ZFS with consumer SATA drives is the best option for my storage needs both at work and at home. The Seagate ST4000DM000 represents a particularly good value and has been proven reliable over the years. I've used RAID Z2 in 6 drive VDEV and RAID Z3 in 8 drive VDEV depending on the use case (up to 36 drives in a single machine).

A few other notes, like people have already said RAID is not backup. Hard drives will inevitably die so in a sense you're just leasing them until the warranty is up. If the drives that died were 500GB drives I'm guessing they were pretty old so you got your money's worth and then some. With ZFS it's easy to move the entire file system and all accompanying data like snapshots to a pool of new drives so updating the hardware over the years isn't a big deal. If you decide to go with something that has RAID like features (be it RAID or ZFS) plan on two or more parity (like RAID Z2 or RAID 6). Single parity is not really sufficient these days with such large drives that are barely faster than drives from a decade ago so the rebuild times can be very long and greatly increase the risk of losing another drive during the rebuild time.

---

