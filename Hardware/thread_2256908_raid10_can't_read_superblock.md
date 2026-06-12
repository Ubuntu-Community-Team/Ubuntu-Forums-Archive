---
title: "raid10: can't read superblock"
date: 2014-12-15
forum: Hardware
---

### Post by PartisanEntity on 2014-12-15
Hi all,

Up until a few minutes ago I had a functioning raid 10 device (/dev/md0) consisting of 4 x 3TB disks.

My operating system (ubuntu server 14.04.1 lts) is mounted on a 120GB SSD seperate from the raid.

I was reading about noatime and that it is good for SSDs (i am new to ssds) so I edited /etc/fstab to add "noatime" to my ssd entry.

I then tried rebooting the headless server and it would hang during boot because it could not mount my raid /dev/md0 under /mnt/raiddisk

Now I have booted by skipping the mounting of the raid device.

cat /proc/mdstat says:

> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[3](S) sdc1[2](S) sdb1[1](S)
      8790402048 blocks super 1.2
       
unused devices: <none>

There is one disk missing in the above list, there should be also sde

Trying to mount manually using "sudo mount /dev/md0 /mnt/raiddisk" gives the following output:

> mount: /dev/md0: can't read superblock

Any help would be appreciated. I have no idea what else to do/try as I am also new to raid in general.

---

### Post by PartisanEntity on 2014-12-15
After some further reading, I tried this:

sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

And got this message:

> mdadm: /dev/sdb1 is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping
mdadm: /dev/md0 is already in use.

So I stopped /dev/md0 and tried again and this time it seems to have worked:

> mdadm: /dev/md0 has been started with 4 drives.

Now cat /proc/mdstat gives:

> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid10 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      5860267008 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      
unused devices: <none>

I was now able to mount it at /mnt/raiddisk

What else can I check/test to make sure all is working right and any ideas what could have caused this?

---

### Post by PartisanEntity on 2014-12-15
Tried restarting and again it hangs during boot, for some reason the monitor I have attached to the server cuts off the left side of the text but I can see the error message:

> ..e for /mnt/raiddisk is not ready yet or not present.
.. to wait, or Press S to skip mounting or M for manual recovery

---

### Post by PartisanEntity on 2014-12-15
Sorry for the monologue, but I was able to fix it.

Upon inspecting the output of sudo parted -l and cat /proc/mdstat as well as looking in /etc/mdadm/mdadm.conf I noticed that the device labels for the harddisks seem to have changed after I tried adding noatime in /etc/fstab.

My ssd used to have the label /dev/sda this then changed to /dev/sde

So md could not auto assemble the raid array upon boot because it could not add /dev/sde to the raid as this was now the ssd for the boot partition.

Upon updating mdadm.conf and addingt the updated disk labels and then running update-initramfs -u I was able to reboot normally and the raid array is assembled and mounted.

But I have no idea why simply adding "noatime" to my ssd entry in /ect/fstab did this.

I have since removed noatime from my /etc/fstab as I am terrified of this happening again.

Any idea why this happened and how I can safely added "noatime" to my /etc/fstab ssd entry without going through all this again?

---

