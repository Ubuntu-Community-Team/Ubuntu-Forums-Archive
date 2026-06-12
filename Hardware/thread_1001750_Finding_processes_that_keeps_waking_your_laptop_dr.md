---
title: "Finding processes that keeps waking your laptop drive using iotop, then what?"
date: 2008-12-04
forum: Hardware
---

### Post by korpenkraxar on 2008-12-04
Hi all!

Having used GNU/Linux OSes for eight years now, I finally took the plunge and installed 8.10 on my Thinkpad Z61m and darn is this a good release or what!? Kudos to the Ubuntu and Debian teams and all other projects that make this nice computing experience possible.

However, just like many others around here I have the curse of the insomniac ticking laptop disk drive that has troubles doing the right thing. I've tried these two (not really knowing which is the recommended method):

/usr/sbin/laptop_mode start
/etc/init.d/laptop-mode start

and also upped the commit-time for my ext3 disk partitions to 600, which seems to help reducing the power cycles. I have also checked the various bash scripts around this forum but not tried them yet.

So I basically wonder what is the general consensus around here for having the drive sleeping at least 5-10 minutes while on battery power?

I installed iotop to check which processes on my system that is actually waking the disk up and interestingly it is only these two that does something with the disk on a regular basis:

gdm
gnome-power-manager

I can't see how any of these guys are really doing something useful with the disk, so does anyone have an idea how disk reading/logging can be turned off for them?

---

### Post by mikewhatever on 2008-12-04
This thread may be helpful -> [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998).
I think setting ext3 to commit=600 is of no use, because it would write every 6 seconds as opposed to the default which is 5, commit=6000 looks better. For instructions on putting your disk to sleep see post #9 of the above linked thread.

---

### Post by korpenkraxar on 2008-12-04
> **mikewhatever said:**
> This thread may be helpful -> [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998).
I think setting ext3 to commit=600 is of no use, because it would write every 6 seconds as opposed to the default which is 5, commit=6000 looks better. For instructions on putting your disk to sleep see post #9 of the above linked thread.

Thanks mate! As far as I've understood the unit for commit is really seconds when dealing with etx3 in /etc/fstab whereas it is centiseconds in /etc/sysctl.conf but I could be wrong.

---

### Post by sdennie on 2008-12-04
> **korpenkraxar said:**
> Thanks mate! As far as I've understood the unit for commit is really seconds when dealing with etx3 in /etc/fstab whereas it is centiseconds in /etc/sysctl.conf but I could be wrong.

That's correct.  

On battery, unless I do an uncached read, my disks usually stay down for 5-10 minutes using a mix of the guide linked above and this one: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773).  However, there is more to it than that because some applications will force disk writes and wake the disks up.  The biggest culprits of unnecessarily waking up the disks are Firefox (which will wake them up after every single page is loaded) and pidgin (which I measured to be about every 3 minutes in my case).

You can fix the Firefox/pidgin problems but in a potentially dangerous (and certainly painful) way by mounting ~/.mozilla and ~/.purple as tmpfs, having /etc/rc.local populate them from a backup copy (and change permissions) and then having a cron job to write the tmpfs diffs back to the backup every 10 minutes.  It can be done but, it's error-prone and not something to be undertaken lightly.

---

### Post by korpenkraxar on 2008-12-05
> **vor said:**
> That's correct.  

On battery, unless I do an uncached read, my disks usually stay down for 5-10 minutes using a mix of the guide linked above and this one: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773).  However, there is more to it than that because some applications will force disk writes and wake the disks up.  The biggest culprits of unnecessarily waking up the disks are Firefox (which will wake them up after every single page is loaded) and pidgin (which I measured to be about every 3 minutes in my case).

You can fix the Firefox/pidgin problems but in a potentially dangerous (and certainly painful) way by mounting ~/.mozilla and ~/.purple as tmpfs, having /etc/rc.local populate them from a backup copy (and change permissions) and then having a cron job to write the tmpfs diffs back to the backup every 10 minutes.  It can be done but, it's error-prone and not something to be undertaken lightly.

Hmm, sounds like something that should be worked on upstream by the developers of each project.

---

### Post by mikewhatever on 2008-12-05
> **korpenkraxar said:**
> Thanks mate! As far as I've understood the unit for commit is really seconds when dealing with etx3 in /etc/fstab whereas it is centiseconds in /etc/sysctl.conf but I could be wrong.

Ah, I see, so your intention is for the filesystem to commit every 600 secs. Sorry for the wrong advice.

---

### Post by sdennie on 2008-12-05
> **korpenkraxar said:**
> Hmm, sounds like something that should be worked on upstream by the developers of each project.

Yes, I agree.  My solution is just a workaround because it doesn't look like that's going to happen anytime soon (at least for Firefox).  The Firefox bug can be found here: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009)

---

