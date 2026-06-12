---
title: "Partition Image restoration w/ Linux"
date: 2008-10-21
forum: General Help
---

### Post by AnalogMan on 2008-10-21
Okay, here is my goal: To Make a clone image of my Windows XP partition, and restore this partition from another partition on the same drive.

My setup:
Grub for the bootloader
Partition 1: 30GB - Windows XP ~10GB used
Partition 2: 80GB - Random storage
Partition 3: 40GB - Linux Distro (Copy of a live CD)

I have GRUB show the two boot options (Windows XP, or my HDD based Live Linux distro) that I can pick from.

My goal is to make an image of my XP partition (I would prefer only the parts that are used but a full partition clone is acceptable) and store it on my linux partition. If the need arises I can format my Partition 1 and restore the partition from Partition 3 from the image.

Anyone know of a linux tool or distro designed for this? I read a lot about dd, but that makes a full disk image including the MBR and FS, which I don't need. Windows XP is a little funky so I don't suppose I could just GZIP the whole partition and extract it after a partition format, could I?

What about PartImage? Does that do just partition cloning and restoration to the SAME disk?

PS. The reason I use a live CD version of a linux distro rather than a HDD install is so it runs in RAM and can't be f*cked up.

Any insight from people who deal with cloning would be ideal. I've also been looking into Clonezilla but would prefer a full functioning Linux distro so if the Windows install is f*cked I can still try and backup some files from that partition even if it won't boot.

---

### Post by geirha on 2008-10-21
dd can make an image of that partition. E.g
```

# From partition to image
dd if=/dev/sda1 of=winxp.image
# From image to partition
dd if=winxp.image of=/dev/sda1

```
The resulting file will of course take the same size as the partition, though compressing it with gzip or bzip2 may help on that.
```

# From partition to image
dd if=/dev/sda1 | gzip >winxp.image.gz
# From image to partition
zcat winxp.image.gz | dd of=/dev/sda1

```
Another possibility is to archive the content of the filesystem with tar
```

# Assuming the winxp filesystem is mounted at /media/windows
cd /media/windows && tar jcf /path/to/windows-backup.tar.bz2 ./
# And to extract on a newly formatted filesystem:
cd /media/windows && tar jxf /path/to/windows-backup.tar.bz2

```
Though I'm not sure if windows will be bootable after just copying files like that.

---

