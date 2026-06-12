---
title: "Hard disk lockups"
date: 2012-11-15
forum: Hardware
---

### Post by awacs on 2012-11-15
... system has random lockups, while rsyncing from disk 1 to disk 2. Obvious suggestion is that the disk is going bad - but which disk?

Complicating issues is the fact that the server is headless, and it would be very inconvenient to hook up a monitor.

Can anyone suggest an easy way to test which disk is locking up?

Thanks!

---

### Post by ahallubuntu on 2012-11-15
Install smartmontools.  Then do

```
sudo smartctl -a /dev/sda

```

to check attributes of /dev/sda (or replace with /dev/sdb, etc.)  It's less easy to interpret the attributes if you don't know which ones are important (the "pre-failure" text looks scary but isn't).  Just paste the output of the command here for the disk you are worried about.

You can also run S.M.A.R.T. tests.

---

### Post by awacs on 2012-11-15
> **ahallubuntu said:**
> Install smartmontools.  Then do

```
sudo smartctl -a /dev/sda

```

to check attributes of /dev/sda (or replace with /dev/sdb, etc.)  It's less easy to interpret the attributes if you don't know which ones are important (the "pre-failure" text looks scary but isn't).  Just paste the output of the command here for the disk you are worried about.

You can also run S.M.A.R.T. tests.

Thanks!

---

### Post by awacs on 2012-11-15
Thanks for anyone who wants to look at this. output of smartctl -a is attached (or I could post it inline if anyone wants.)

---

### Post by ahallubuntu on 2012-11-15
The 250GB WD drive (/dev/sda) has four reallocated sectors.  That means four sectors failed and were marked "do not use" by the drive's firmware and replaced by spare sectors.  This is not catastrophic especially on an old drive.  You may see a slight reduction in performance as the spares will be non-contiguous with the sectors that failed.

You should watch this number, though; if more sectors fail more than say a few a year I'd replace the drive.  The drive probably has a few hundred spare sectors FYI.

None of the other drives have glaring problems that jump out at me.

You can use smartctl to run an extended S.M.A.R.T. test on the drives that are suspect.  On the 250GB drive the test will take probably 1-2 hours.  Check the man page for smartctl for exact syntax.  The drive itself (the firmware) will run the test; smartctl will just monitor its progress each time you check it.  You can use the drive while the test is in progress but probably best not to.

---

### Post by awacs on 2012-11-15
Thanks!

---

### Post by Doug S on 2012-11-16
When your system locks up, how long does it lock up for? Is it 30 seconds?
Are there any entries in /var/log/kern.log when the lock up occurs?

---

### Post by awacs on 2012-11-16
Locks up 'forever'. Need to power cycle. No messages at the time of lockup, but at other times I get messages like
'NMI backtrace for cpu 2'
in kern.log.

---

### Post by Doug S on 2012-11-16
Thanks. Then your issue is different than [mine]("http://www.smythies.com/~doug/network/hd_race/index.html"). For my issue I have traced it back to a single line change in udev between launchpad versions 2759 and [2760]("http://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu/precise/udev/ubuntu/revision/2760/debian/patches/builtin-block-polling.patch"). I have yet to find someone else experienceing the same issue.
Hope you get yours figured out.

---

### Post by ahallubuntu on 2012-11-16
Go ahead and run the extended S.M.A.R.T. test.  But there are lots of reasons a system could lock up that have nothing to do with the hard drives.  The CPU could be overheating.  The power supply could be suspect.  The RAM may have an issue.  Same with the motherboard.

---

