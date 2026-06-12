---
title: "Adding a disk to an existing filesystem?"
date: 2005-11-16
forum: General Help
---

### Post by ed_d on 2005-11-16
Is this possible to do or do I have to create another filesystem? Any help would be great. Have a disk that I created at install called "multimedia that I have all my isos and music on and would like to add another disk to it. Thanks for any help.

---

### Post by Kyral on 2005-11-16
You mean like installing another HD?

---

### Post by ed_d on 2005-11-16
Yes. I have 1 36gb disk that may fill up soon, and would like to add another 36gb drive to that filesystem.

---

### Post by Kyral on 2005-11-16
Assuming its installed (Hardware style, plugged into the mobo, that kinda thing) you have to format it first. What you would need to do is find out where in the /dev (device) tree it is. Most likely something like hda, hdb, sda, etc. Easiest way to do this is to do

```
sudo fdisk -l
``` before and after you install the disk to see what was added to the listing. Once you have that you can format it with either GParted/QtParted (PartitionMagic clones) or FDisk and the mkfs commands(Ask me if you need help). After that make a mountpoint

```
mkdir <whereever you want to mount it>
```

Then add it to FStab with

```
sudo gedit /etc/fstab
```

The format for the line is

```
<device> <mountpoint> <fs> defaults, users,rw 0 0
```

Save it and away you go

---

### Post by ed_d on 2005-11-16
OK, so the way you have described will add a disk, then create a new filesystem, right? I wonder if there is a way to just add the disk to an exsisting fs, as in extend the fs to another drive (grow the fs).
I have a x240, so I can add the drive fairly easily to the system physically, and I can add another fs logically.
I know how to extend a lv within AIX, but this is different. I can always just add a new fs called ISOs too.

thanks

---

### Post by Lambert on 2005-11-16
Doing what kyral said does add the device into the file tree. Where on windows if you added the drive it would show up like F: drive or something else in linux it just shows up where you mount it (/mnt/hdbX).  You can mount it just about anywhere you want I believe, (but not completely sure)

Of course though there are places you won't want to put it like /etc. Usually /mnt is where I see drives mounted.

---

### Post by darknuala on 2005-11-16
Other than what they've said, you could manually do it during install using the LVM.  Of course it works both ways.

---

