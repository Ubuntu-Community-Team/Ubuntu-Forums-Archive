---
title: "Computer doesn't see hard drive"
date: 2015-06-07
forum: Hardware
---

### Post by asb3 on 2015-06-07
I rebooted my computer after performing software upgrades.  My computer has 4 hard drives.  After the latest reboot, it doesn't see the 1T drive which contains most of my data. When I reboot, I get the error message

The disk drive for /mnt/hd1 is not ready yet or not present.

Is this a probable hardware failure?

---

### Post by oldfred on 2015-06-07
Did you have an abnormal shutdown? 
That can cause file corruption and you may only need a fsck.
But you should check in Disks and upper right corner star icon for more, and look at Smart Data Status. It can run lots of tests, but all I know is passed is good and anything else is not.

If booting from another drive, then you do not have to use the live installer. Just that the partition must be unmounted.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by weatherman2 on 2015-06-07
I prefer GSmartControl to check S.M.A.R.T. status and run tests.  GSmartControl is easy to install in Ubuntu.

Check the S.M.A.R.T. Attributes of the hard drive in question - see if any are highlighted in red.  (Some Attributes are classified as "pre-failure" but that's just the type of data field it is.)  Of course, your drive has to be detected at all to check S.M.A.R.T. status.  Hard drives do fail now and then.

---

### Post by asb3 on 2015-06-07
The drive is not detected.

---

### Post by tgalati4 on 2015-06-07
Check the cabling.  Make sure everything is seated tight.  If the drive is not spinning, then it's possible that it is worn out, however, a disk that is slow to spin up is usually recoverable.  Can you boot into BIOS and see the drive?

---

### Post by asb3 on 2015-06-07
I checked the cabling; it seems to be OK.  BIOS doesn't see the drive.

---

### Post by weatherman2 on 2015-06-07
Unfortunately, the drive controller may have failed.  Does the drive seem to spin up up?  Do you feel a vibration on the drive?

Have you tried swapping the cables with those of one of the other drives?

---

### Post by asb3 on 2015-06-08
I think I have a hardware failure.  A startup, the drive makes a clicking noise for a short time before stopping.  I guess I'll have to send it to a data retrieval service.

Alan

---

