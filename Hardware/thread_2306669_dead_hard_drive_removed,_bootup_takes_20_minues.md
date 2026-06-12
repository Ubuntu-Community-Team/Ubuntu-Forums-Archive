---
title: "dead hard drive removed, bootup takes 20 minues"
date: 2015-12-17
forum: Hardware
---

### Post by pickarooney on 2015-12-17
One of my three SATA hard drives failed earlier today (it was a data only drive) and it took me forever to get the PC to boot up at all, then locate the damaged drive, try in vain to repair it and ultimately disconnect it and remove it from fstab.
Now, however, bootup takes 20 minutes with the remaining drives. Instead of the Ubuntu splash screen I have two lines of fsck information and a loooong wait before it boots up.

What can I do it restore fast booting? Should I be looking at reformatting the MBR, the bootloader or even the OS? Reconfiguring GRUB? I thought after three reboots it would speed up but it's still taking forever.

---

### Post by SeijiSensei on 2015-12-17
Did you remove the entry for the drive in the BIOS?

---

### Post by weatherman2 on 2015-12-17
> **pickarooney said:**
> One of my three SATA hard drives failed earlier today (it was a data only drive) and it took me forever to get the PC to boot up at all, then locate the damaged drive, try in vain to repair it and ultimately disconnect it and remove it from fstab.
Now, however, bootup takes 20 minutes with the remaining drives. Instead of the Ubuntu splash screen I have two lines of fsck information and a loooong wait before it boots up.

What can I do it restore fast booting? Should I be looking at reformatting the MBR, the bootloader or even the OS? Reconfiguring GRUB? I thought after three reboots it would speed up but it's still taking forever.

Was a partition from the failed drive being automatically mounted in your /etc/fstab ?  If so, you need to remove that line or Ubuntu may wait a while until until it "becomes available" until it gives up.  Removing the line (or just putting a "#" in front of the line to comment it out) would tell Ubuntu not to try to mount that partition any longer.

Is it possible you have other issues?  Did you check the other hard drives?  S.M.A.R.T. status (Attributes) of each drive?

---

### Post by pickarooney on 2015-12-18
The BIOS automatically removes the disconnected drive and I manually commented out the (only) partition of that drive from fstab.

I did see something briefly pop up about SMART when booting, but I think both remaining drives are OK (see attached).

---

### Post by oldfred on 2015-12-18
Depending on which way you boot you can review logs.

 Older systems with Upstart
gksudo gedit /var/log/dmesg
sudo grep -E -i "error|warning" /var/log/dmesg 

   Newer systems with systemd:
systemd-analyze blame

---

### Post by weatherman2 on 2015-12-18
> **pickarooney said:**
> The BIOS automatically removes the disconnected drive and I manually commented out the (only) partition of that drive from fstab.

I did see something briefly pop up about SMART when booting, but I think both remaining drives are OK (see attached).

Those are old drives, and I would personally run the Extended test on both of them, as a precaution.  Could be they are fine, though.

If you've never run a full fsck on the file systems - ?  I'd probably do that too if they are fairly old.

---

### Post by pickarooney on 2015-12-18
systemd-analyze blame 
gives this

 9min 19.213s systemd-fsck@dev-disk-by\x2duuid-6b3d3bf6\x2d9e85\x2d4680\x2d9

before a load of normal stuff taking a few seconds each.
I'd prefer if it didn't fsck every time I booted.

---

### Post by oldfred on 2015-12-18
Try this on your ext4 partitions:

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by yoshii on 2015-12-18
what happened with your fstab?

---

### Post by pickarooney on 2015-12-27
I've been away for a week, so just got around to trying this now.

I tried this

sudo e2fsck -C0 -p -f -v /dev/sdc1

and it got to 1.0% and gave the error
```

Error reading block 3407874 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

Gigantor: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

```

So I ran the second command 

sudo e2fsck -f -y -v /dev/sdc1 

and it took about an hour finding and fixing bad blocks before it finished and disconnected the hard drive.
I rebooted and /dev/sdc was there again but I'm still unable to get beyond 1% on running the first command before it cuts out with the same error.

---

### Post by weatherman2 on 2015-12-27
Did you run extended S.M.A.R.T. tests on the remaining hard drives or not?

---

### Post by pickarooney on 2015-12-27
This is the result of the SMART test on drive hdc

Probably just dead, yeah?

---

### Post by oldfred on 2015-12-27
It says passed, but that you have never run any tests. 
I would run either short or even longer test & see if it still says passed.

---

### Post by weatherman2 on 2015-12-27
You've got 43 pending sectors (sectors that can't be read).  And S.M.A.R.T. errors are being logged now.  So yeah, looks bad.  I'd replace that drive, too.

---

