---
title: "New to SSD - fresh install"
date: 2014-08-13
forum: Hardware
---

### Post by steve7777777 on 2014-08-13
My system is currently Ubuntu 10.04 so time to upgrade the OS to 14.04. I figured if I was going to re-install everything as opposed to upgrade why not get an SSD drive? So I have a **SAMSUNG 840 EVO MZ-7TE250BW 2.5" 250GB**  on the way from Newegg!

I'm using suggestions from:  [COLOR=#1155CC]_[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)_[/COLOR]

-7% of the drive will be unpartitioned - not formatted.
-I'll leave 20% free so EXT4 journaling can do it's thing.

I'll have various virtual machines but those will be stored on a different (non-ssd) hard drive.

I want to keep i simple, so everything except data will go on the SSD. In other words the /home will be on the SSD.
I have four other (non-ssd) drives (JBODs) -** so will use the FSTAB from the 10.04 installation on the new 14.04. Is this OK?**
My big question - **can I continue to use Clonezilla for backup - to create disk image? If the SSD fails I'd like to restore from an image to the replacement SSD.**
Any other suggestions or do you have better more current advice? Do you agree with [COLOR=#1155CC][FONT=Arial][U][https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

[/U][/FONT][/COLOR]Thanks!

---

### Post by weatherman2 on 2014-08-13
If you are re-installing Ubuntu, install on an LVM so that you can make snapshots of your OS partition while booted, then backup the snapshot.  So you don't have to shut down and boot up separate software like Clonezilla to make backups.  Make them while the OS is running.

If I make my OS ("/") partition 20GB, I leave say 1GB free in my LVM, then I can allocate that to a snapshot.  My backup script creates the snapshot of /, backups the snapshot, then deletes the snapshot.  You can use tar, rsync, whatever you want to make a backup of the snapshot of /.

LVM is built into the Ubuntu 14.04 installer now and is an option when installing.

I don't worry too much about the health of my SSD drives.  A lot of the potential hazards you read about with SSD drives may no longer be relevant as drive technology has improved. And with prices coming down so fast now, in 2-3 years you should be able to buy a much faster, larger SSD to replace this one which may become obsolete before it ever experiences any problems.

---

### Post by TheFu on 2014-08-13
One of your sentences doesn't make sense - can you please re-read and perhaps edit it? It reads to be exactly the opposite of what you seem to intend.

> I want to keep i simple, so everything except data will go on the SSD. In other words the /home will be on the SSD.
What do you store in /home, if not data?

I can't imagine why clonezilla wouldn't continue to work, but I think there are much better options than image-based backups. There are many long threads here on that topic.  If you need an image, I'd rather see fsarchive used, since it can restore to smaller or larger new storage.  I don't do image-based backups - hard to do those automatically and I'm too lazy to manually do backups. Mine are 100% automatic using **rdiff-backup** - nightly. 60-120 days of backups lets me sleep REALLY, REALLY well and only uses about 1.2x the storage of the source files. If /home is 1G, then 60 days of versioned backups is about 1.2G ... how cool is that?  Of course, it depends on how much data changes daily, but that is under your control - as are the number of days to retain versions.

For backups, don't store the OS. After all, we have an ISO that can be booted and installed. Then just restore the settings, core data, list of programs installed and large data (as time permits). That saves about 4G off every OS that doesn't need to be backed up - which ripples through the entire infrastructure:
* less storage
* less time doing backups
* less time doing restores
* always current
Plus it means that a restore or migration to different hardware is just an install (10-15min), restore setting and critical data (5-10 min), then tell the OS which packages should be installed from a backed-up list (2 sec), then tell it to install (we have apt-cacher-ng here, so all package installs are from LAN storage) which is 5-15 minutes.  In 30-45 minutes, a crashed system can be rebuilt onto new hardware.  Clearly, if there is 5TB of data, that will take more time to get back, but the core 20G is done in less than 1 hour.

The main things for SSDs is the noatime option on mounted partitions and running trim periodically. There is a crontab for that on my system with an SSD. I didn't create it or write it. The installer did it.  Just for fun, ran
```
$ sudo fstrim -v /Data
/Data: 17572913152 bytes were trimmed
$ sudo fstrim -v /
/: 64577384448 bytes were trimmed
```
Things were a little flaky after - had to reboot.

Why they have people install an editor that NOBOBY uses, I don't understand?  Use whatever editor you like, but know that GUI editors run under elevated privilege (sudo) might save preferences with root ownership.  vi doesn't do this and I suspect that nano won't either.

---

### Post by steve7777777 on 2014-08-13
> **TheFu said:**
> One of your sentences doesn't make sense - can you please re-read and perhaps edit it? It reads to be exactly the opposite of what you seem to intend.

I can't imagine why clonezilla wouldn't continue to work, but I think there are much better options than image-based backups. There are many long threads here on that topic.  If you need an image, I'd rather see fsarchive used, since it can restore to smaller or larger new storage.  I don't do image-based backups - hard to do those automatically and I'm too lazy to manually do backups. Mine are 100% automatic using rdiff-backup - nightly. 60-120 days of backups lets me sleep REALLY, REALLY well and only uses about 1.2x the storage of the source files.

The main things for SSDs is the noatime option on mounted partitions and running trim periodically.
setting.
```
$ sudo fstrim -v /Data
/Data: 17572913152 bytes were trimmed
$ sudo fstrim -v /
/: 64577384448 bytes were trimmed

```

Why they have people install an editor that NOBOBY uses, I don't understand. Use whatever editor you like, but know that GUI editors run under elevated privilege (sudo) might save preferences with root ownership.  vi doesn't do this.

Clonezilla - yes I wanted to know if it works with SSD. Restoring image to SSD without need to reinstall. 
Which sentence doesn't make sense?

---

