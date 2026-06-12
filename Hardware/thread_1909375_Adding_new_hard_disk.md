---
title: "Adding new hard disk"
date: 2012-01-15
forum: Hardware
---

### Post by theKuch on 2012-01-15
I added a new hard disk to the system.

How do I find it in order to mount it.

Thanks.

---

### Post by kc1di on 2012-01-15
First a couple of questions:
1. How is the new drive partioned formated?
2. Does it appear on the boot up list when you first turn your computer on  (Did you make sure your Bios has found the drive you installed?)

---

### Post by coldraven on 2012-01-15
You might need to format it first.
Try running the Disk Utility, your drives should show up in the left hand pane.
Look at your old drive and note what formating it has in the main Linux partition.
Then select the new drive and click the format button.
If your existing drive is formatted ext4 then you should format the new one the same.
Whether you want to make one big partition or several smaller ones is up to you.
Then try re-booting and see if it auto mounts.

You do have a backup in case you mess up, don't you?
If you format the wrong drive all your data will be lost.

---

### Post by theKuch on 2012-01-15
Thanks.

I'm running KDE Partition Manager 1.03

I have located the new disk.

"No valid partition was found on this device"

Do I run "New Partition Table" from the device menu?

Yes, I am backed up -- thanks.

---

### Post by kc1di on 2012-01-15
> **theKuch said:**
> Thanks.

I'm running KDE Partition Manager 1.03

I have located the new disk.

"No valid partition was found on this device"

Do I run "New Partition Table" from the device menu?

Yes, I am backed up -- thanks.

Do not run new partition table.
instead go to look for gparted I'm using xubuntu at the moment so can't tell you were it is in ubuntu. run it and partition the new drive the way you want. then reboot see if it finds the new partitions.

---

### Post by theKuch on 2012-01-15
Thanks Dave.

I set up a partition of the entire drive. When I rebooted I can see it gparted marked as /dev/sdb and unallocated.

Do I need to format?

---

### Post by kc1di on 2012-01-15
> **theKuch said:**
> Thanks Dave.

I set up a partition of the entire drive. When I rebooted I can see it gparted marked as /dev/sdb and unallocated.

Do I need to format?
yes you should put what ever filesystem your using I don't know how big the drive is if you said i've forgotten. but if it's quite big you may want to partition it in more than one partition. If you are planning on using it for your ubuntu install you will also need to name it.  something like /extra or whatever you want. 

good Luck,
Dave

---

### Post by theKuch on 2012-01-15
I just want to use it for data -- photographs actually.
It's 1 tera. I'd prefer to use the whole disk as a single partition.

I have another disk which is 500 GB unpartitioned, and a third disk which is partitioned for Ubuntu with another partition for data.

The 500 drive is "ext3" as is the data part of the 3rd disk.

So I should add the new dis as "ext3" as primary partition?

Thanks for walking me through this.

Menachem

---

### Post by theKuch on 2012-01-15
The new disk is showing, but I can't copy to it because I do not permissions.
How do I set permissions? I did chmod as su but that didn't help.

Also when I boot up, the disks are not accessible, not showing ion the sidebar. I hit open in the browser for example, and just touch the disk names without actually opening anything. The icons then appear on the side bar.  How do I get this to happen on its own?


Thanks

---

### Post by theKuch on 2012-01-15
OK -- managed to chmod and write to the "new" disk.

---

