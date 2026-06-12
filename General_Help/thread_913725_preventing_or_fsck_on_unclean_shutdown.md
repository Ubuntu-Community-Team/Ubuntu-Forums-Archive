---
title: "preventing or fsck on unclean shutdown"
date: 2008-09-08
forum: General Help
---

### Post by yacwroy on 2008-09-08
Hi

I know there are many ways to prevent fsck performing its auto-checks. However I can't seem to find any way to stop fsck running after an unclean shutdown (on / and /boot partitions). Of the 100s of posts I find about preventing fsck, they're all about disabling "check on N reboots / days".

Is there any way I can do this?

If not, would it be possible to prevent this by forcefully uninstalling fsck, or would that prevent Ubuntu from booting?


NOTES:
Unfortunately I know that many people here will want to reply with "but you should check because there might be something wrong". So just to preempt those messages, I want to stop fsck from EVER checking on startup, and I don't care about any consequences. It's more efficient for me to take my chances that nothing is wrong (and re-install if necessary) than to check my drives at startup. 

The / and /boot drives get flagged as "needs to be checked" by a windows ext mounter occasionally on shutdown (and yes I do want to see these partitions from windows), or when linux or (rarely) windows crashes. fsck never finds anything wrong, and just wastes boot time and increases HDD wear. And the ubuntu people have yet to add an ESC option to cancel checking on unclean shutdown.


Thanks.

SPECS IF NEEDED:
Ubuntu 64-bit.
Release: 8.04 hardy.
Kernel: 2.6.24-19-generic
CPU: Intel Core 2 Duo.
File system: ext3

---

### Post by yacwroy on 2008-09-10
Going to bump this just once, sorry.

---

### Post by kerry_s on 2008-09-10
sudo gedit /etc/fstab

change the last number to 0
example:
```
/dev/hda2       /               ext2    noatime,errors=remount-ro 0       1
to
/dev/hda2       /               ext2    noatime,errors=remount-ro 0       **0**
```

or 
not sure if it still works
sudo gedit /etc/default/rcS

change:
FSCKFIX=no
to
FSCKFIX=yes

a little advice, leave it alone, if it does get corrupted from a unclean shutdown, you can totally destroy it by skipping the check.

---

### Post by Faolan84 on 2008-09-10
If you do this you should also note that you should do a manual check every once and a while and do a back up of your data weekly or every other week because **** happens and it's best not to get caught with your pants down. Also note that when you run fsck you need to make sure that the drive you are running it on is *NOT* mounted. That is why fsck runs at bootup.

---

### Post by yacwroy on 2008-09-10
All my drives are already 0'd in etc/fstab for the last column, but this is ignored for unclean shutdowns, it seems.

I don't think FSCKFIX helps, it simply runs fsck with -y if I read correctly.

================

Isn't the purpose of a journaling FS like ext3 to prevent unexpected shutdowns from causing inconsistencies. What are the actual chances an ext3 partition getting corrupted when an active write to the partition is unexpectedly halted via reset or something. The likelihood should be pretty low, meaning fsck really shouldn't be run on unclean shutdowns. I guess stats for this would be hard to find, though.

My drives are constantly getting unclean shutdowns from unexpected resets and Ext2IFS forgetting to unmount on shutdown, and I never find any issues, although /boot wouldn't be modified except on kernel upgrades etc, and / doesn't get too much work.

================

I would occasionally fsck overnight, probably via CD, if I didn't have it running approx every 3rd boot for 5 mins.

As for backups, my important data isn't on / or /boot, my code is always backed up to gmail & elsewhere, and my large files are duplicated on backup drives that are usually not plugged in.

---

### Post by amo-ej1 on 2008-09-10
Quoting wikipedia "Such file systems are less likely to become corrupted in the event of power failure or system crash." and min the 'less likely' in that sentence. 

But if you open /etc/init.d/chreckroot.sh near line 210 you will encounter this snippet: 

```

	#
	# See if we want to check the root file system.
	#
	FSCKCODE=0
	if [ -f /fastboot ]
	then
		[ "$rootcheck" = yes ] && log_warning_msg "Fast boot enabled, so skipping file system check."
		rootcheck=no
	fi

```

meaning a sudo touch /fastboot might do the trick

---

### Post by kerry_s on 2008-09-10
> every 3rd boot for 5 mins.

it should be 30 startups, not 3, i would say your install is already going funky.

---

### Post by Faolan84 on 2008-09-10
Ext3 is a pretty sturdy file system. I've used it since it came out and before that I used Ext2 which I only had a couple very fixable problems. However, that being said that does not mean that something very bad might happen and you are in a position where you can't fix things that would have been fixable had you caught it sooner. If you're constantly finding errors on your fsck runs then it may be a sign that something is wrong with your hard drive and you should back up all your data and look into having it replaced. That is usually a sign that something is about to go seriously wrong.

That being said, I work on plenty of people's computers on the side for money and I can definitely say that you should try to avoid shutting down your system uncleanly if it is at all possible and also take note that if you're getting lots errors on your fsck runs you need to make a mental note of it if it is reoccurring.

That being said if you are using JFS or XFS make sure that you don't shut down you're system unclean because these file systems are more prone to dropping larger chunks of data than Ext3 and you should make sure that you don't disable fsck on these because i've heard numerous horror stories of data loss on JFS and XFS that came from no doing regular fsck runs and unclean shutdowns.

---

### Post by amo-ej1 on 2008-09-10
Oh i'm pretty sure every filesystem breaks, several years ago i've lost a couple of systems due to ext3 death.

Nevertheless, there are some occasions where you simply not do an unclean shutdown. For example if you're developing applications which use a hardware watchdog, a bug in the application might cause the watchdog to trip. If you are on experimental hardware you kernel might lock up due to driver bugs/featuers, if you're developing kernel modules you might very easily cause your system to lock. When you're developing applications with realtime priorities you might lock yourself out as well etc etc

---

