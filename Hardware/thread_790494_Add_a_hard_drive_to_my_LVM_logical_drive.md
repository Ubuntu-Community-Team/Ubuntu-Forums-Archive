---
title: "Add a hard drive to my LVM logical drive"
date: 2008-05-11
forum: Hardware
---

### Post by Jordanwb on 2008-05-11
Last night I put two Maxtor hard drives (virtually identical), both 40 GB into this old computer of mine. Formatted both drives and set up 8.04 Server with LVM. Now it set up one disk for the Logical Drive but not the other. What do I need to do to combine the two drives together?

Thanks.

---

### Post by srimalik on 2008-05-11
you can add multiple disks to a volume group(VG) and then create LVs on that VG.

The steps would we:

1. Create PVs on both the harddisks ( see 'man pvcreate' )
2. Create a single VG containing both the PVs ( see man vgcreate)
3. Create LVs on the VG ( man lvcreate)

hope this helps.

---

### Post by Jordanwb on 2008-05-11
On the drive that I want to add there are no partitions on it. So would I need to create a ext3 partition?

It seems like I'm not the only one having problems: [http://ubuntuforums.org/showthread.php?t=571292](http://ubuntuforums.org/showthread.php?t=571292)

---

### Post by Jordanwb on 2008-05-11
Okay here's what I did through Putty (exactly)

dir /dev (To find out the path of the second drive, it is /dev/sdb)
sudo lvm
pvcreate /dev/sdb
vgextend SERVER /dev/sdb
vgdisplay

Now it shows that the size of the logical group is ~80GB, however a few lines down it says:

Alloc PE / Size     9740 / 38.05 GB
Free  PE / Size     9801 / 38.29 GB

I think I did something wrong.

---

### Post by srimalik on 2008-05-11
What you did seems correct to me. Whats the problem now?
Are you not happy with Free PEs ? If so, create a lv on this vg it will consume the free PEs.

Or Are you worried about the ~3.7 GB  which seems to be lost? I think its expected. I have a 40GB HDD with me but can only use 38 GB of it :(.
May be some metadata is stored on it or there is some trade off in interpreting a KB ( 1000 bytes 1024 bytes) 

-Sri

---

### Post by Jordanwb on 2008-05-12
Well the reason I think something is wrong because I don't understand these lines:

Alloc PE / Size 9740 / 38.05 GB
Free PE / Size 9801 / 38.29 GB

If that's what is supposed to happen then my concern in unneccisary.

I know why I don't get the full 40 GB. The reason why it says 40 GB but we get ~38 is the interpretation of a kilobyte. Marketing beleives a kilobyte is 1000 bytes, but it's actually 1024.

---

### Post by Jordanwb on 2008-05-12
I installed TorrentFlux a few minutes ago and it reports as the "drive" being only 38GB big, so I did do something wrong.

I ran this command at the lvm> prompt:

lvextend -L +38.28GB /dev/SERVER/root /dev/sdb

after that I type vgdisplay and it says:

VG Size    76.33 GB
PE Size    4.00 MB
Total PE 19541
Alloc PE / Size   19540 / 76.33 GB
Free PE / Size    1 / 4.00 MB

But torrentflux still reports the drive as being 38 GB.

---

### Post by srimalik on 2008-05-12
Yes the free PEs are expected, When you create/extend a LV on this VG it will consume the PEs(physical extents), The whole space is divided into PEs in your case you have a PE size of 4MB. this means your lv size will be multiple of 4 always.

As you have seen it happening practically, no need to worry.

I don't know whts torrentflux it may be diplaying the actual size of physical drive which is 38 GB(taking 1kB as 1024 bytes).

---

