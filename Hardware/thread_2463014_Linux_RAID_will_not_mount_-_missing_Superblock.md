---
title: "Linux RAID will not mount - missing Superblock"
date: 2021-06-01
forum: Hardware
---

### Post by trisgti2 on 2021-06-01
hi all,
I have an old RAID 5 (I know..) set up on a media server and following a power down am getting the following when I try and mount the raid:

xxx@xxx:~$ sudo mount /dev/md0 /var/data
mount: /var/data: can't read superblock on /dev/md0.

some info on the raid:

xxx@xxx:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd[3] sdc[1]
      5860271024 blocks super 1.2

xxx@xxx:~$ sudo mdadm --verbose --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd
mdadm: looking for devices for /dev/md0
mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted


xxx@xxx:~$ sudo mdadm --verbose --assemble /dev/md0 /dev/sdc /dev/sdd
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdc is busy - skipping
mdadm: /dev/sdd is busy - skipping


running smartctl -d ata -a /dev/sdx against the 3 drives returns: SMART overall-health self-assessment test result: PASSED

is there anyone who can help me out?  I'm ok with terminal but not a linux or raid expert by a long stretch.

thanks in advance!

---

### Post by Autodave on 2021-06-01
"Bad superblock" in 99.9% of the cases means that the HD has failed.  You may be able redo the drive and use it, but I would not trust it again.

---

### Post by SeijiSensei on 2021-06-01
For future reference, it's usually a better idea to combine partitions via mdadm than whole drives.

---

### Post by trisgti2 on 2021-06-01
have got it sorted out now.

I had to stop the raid then zero the superblock on /dev/sdb, assemble with the 2 remaining good drives and add the missing one again.  took 10 hrs to sync but all seems well now.
will run some tests on the drives to see if any need replacing.

---

### Post by trisgti2 on 2021-06-01
> **SeijiSensei said:**
> For future reference, it's usually a better idea to combine partitions via mdadm than whole drives.
thanks, will remember that next time.

---

