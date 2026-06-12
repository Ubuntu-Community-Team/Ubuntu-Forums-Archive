---
title: "Failed HDD. Linux tools to recover the data."
date: 2009-04-29
forum: Hardware
---

### Post by joseraeiro on 2009-04-29
Hi,

The HDD on my laptop failed. I've managed to boot with the ubuntu live CD.

I'm able to mount the partitions on the failed disk, but I get I/O errors (from the failed HDD) while trying to copy the files to a external USB HDD.

Are there any tools to try to fix and/or copy the files from the failed HDD?

Thanks!

---

### Post by AnonCat on 2009-04-29
A program called Testdisk might work for you.  It should be in the repos.  Here's a link:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by damis648 on 2009-04-30
Testdisk is for recoving lost phantom data on a drive and will likely not work with a physically damaged drive. OP, you are looking for ddrescue. This tool will create an image file directly the same as the partition on the dead drive you image, at the same time ignoring all bad sectors and data. Remember, a dead drive is dead and all data may or may not be recoverable. Start by connecting the drive (unmount the partition if it mounts) and opening a terminal and executing the following:
```
sudo apt-get install ddrescue
ddrescue if=/dev/hdxx of=/output/image/file/path.img
```
where hdxx is the block device for the needed partition on the drive and the of= section gives the path to the output file where the partition on the drive will be imaged. (Make sure, of course, that the output drive has enough free space as the total partition size of the old drive). Once that is finished, mount the new drive:
```
sudo mkdir /media/virt
sudo mount -t ext3 -o loop /path/to/image/file.img
```

---

