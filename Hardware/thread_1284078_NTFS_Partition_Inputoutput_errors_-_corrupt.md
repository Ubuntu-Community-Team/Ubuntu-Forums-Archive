---
title: "NTFS Partition Input/output errors - corrupt?"
date: 2009-10-06
forum: Hardware
---

### Post by joehardflec on 2009-10-06
I've got an external drive (well, a desktop IDE drive in a USB enclosure), that's divided into two partitions, both formatted as NTFS. One works fine, while I get input/output errors trying to access some files on the other. 

I can mount the partition and see all of the files, but they cause problems when trying to view or copy them.

Sometimes it gets part way through copying the files and then freezes and gets no further, other times it won't work at all and gives me an input/output error. 

I've tried the drive through the enclosure on both Linux and Windows on my laptop, and get similar problems, and I've also tried removing the disk from the enclosure and using it in a Linux desktop. Same problem. 

Any suggestions for fixing the partition or just recovering the files welcome.

---

### Post by AwesomeTux on 2009-10-06
Try this:

 1. Create a new NTFS partition with Gparted or something (or command-line)
 2. Move files from problematic NTFS to new NTFS (or EXT4 if you wanna switch) using "sudo cp -a [old drive mount point] [new drive mount point]
 3. Check if the new partition works, if so
 4. You can delete the old partition

Be sure the check the NTFS partition for errors (gParted does this during partitioning)

Just my $0.02

---

### Post by joehardflec on 2009-10-06
It seems to have worked for some files and not others. (Eventually gave me an input/output error and seemed to lock up, so I stopped it with ctrl-c. )

I'm deleting the files that worked from the old partition and trying again, see if I get any more sorted.

---

