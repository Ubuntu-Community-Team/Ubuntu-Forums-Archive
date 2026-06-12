---
title: "External eSATA hard drive - slow transfers on fat32, fast on ext3"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by anthropodeus on 2009-04-29
I have a ~500GB external HDD connected to my laptop via eSATA.  There are two partitions on it: a small one that is fat32 and a large one that is ext3.

files transfer to the ext3 partition at normal eSATA speeds - about 33MB/s.  but the transfer speed to the fat32 partition is only around 10MB/s max, and usually slows to around 6MB/s as the transfer proceeds.

if i change the options from the ext3 partition from "relatime" (the default) to "rw,auto,user,sync" so that i can unmount it without going through root, the transfer speeds to the ext3 partition ALSO slow down to ~10MB/s.

so what is it in the "relatime" default that makes mount recognize the connection as full eSATA? and how can i make the fat32 partition transfer at full eSATA speed?

here's the relevant stuff from /etc/fstab:

```

#	<file system>					<mount point>   	<type>			<options>					<dump>	<pass>
#
#External Hard Drive:
#
# /media/Archive was on /dev/sdb3 during installation.
	UUID=2d840736-429e-4984-9f75-7ad1c532c9b0	/media/Archive		ext3			relatime					0	2
# /media/ExternalAudio was on /dev/sdb2 during installation
	UUID=49E2-61B0					/media/ExternalAudio	vfat			rw,noauto,user,sync,shortname=mixed,utf8	0	1

```

---

### Post by logos34 on 2009-04-29
I wonder if it's the way Hal is mounting the vfat partition (vs. an interface issue).  Related discussion [here]("http://ubuntuforums.org/archive/index.php/t-793688.html") (but concerned with USB).  Maybe add the fstab mount options **async** and **flush**

atime vs. noatime and relatime is explained [here]("http://blogs.koolwal.net/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/").  (speed diff in ext3 is due to atime/sync excessive disk writes)

There was another article explaining noatime and relatime that I read some time back (when I was trying to eliminate constant disk activity), but I can't seem to find it now.  hmm

---

