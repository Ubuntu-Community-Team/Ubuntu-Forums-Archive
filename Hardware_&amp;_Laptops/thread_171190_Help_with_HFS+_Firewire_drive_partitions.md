---
title: "Help with HFS+ Firewire drive partitions"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by nzmoose on 2006-05-06
Ok i'm super noob here but i'm trying to go totally opensource, ubuntu rocks and the the community is great but ive got one thing holding me up.

I have this firewire harddrive thats HFS+ because i use a lot of Macs in my work, it has 3 partitions, when i plug it in it registers as "sda" in /dev so thats cool

so i go "sudo mount -t hfsplus /dev/sda /media/test" hunky dory it mounts the first partition no problem. 

How can i mount the other 2 theres no sda1, sda2, sda3 kinda stuff going on. Sorry if this is really obvious but it's got me stumped :-x 

any ideas?

---

### Post by Rizado on 2006-05-06
There are no sda1, 2 etc? That's really odd. What do you see if you run "sudo parted /dev/sda" and then type in print? You can type in help too if you want to see the options.

EDIT: You probably want the hfsplus package installed too. That might just be the problem. Grab it from the repositories.

---

### Post by nzmoose on 2006-05-06
[I]Using /dev/sda
(parted) print
Error: Unable to open /dev/sda - unrecognised disk label.
(parted)[/I]

thanks for the help bus as you can see, it's not having a bar of it, as a sideline the disk is showing up as "unallocated space" in GParted aswell. Do you think it would help if the drive was just plain HFS (no plus)?


*edit*

grg@grg-ubuntu:/$ fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

is this normal?

---

### Post by Rizado on 2006-05-07
You haven't recompiled your kernel have you? Because if you have make sure that you include macintosh partition table support.

Anyway I'm not sure what your problem is really. Making it hfs instead of hfs+ is no good idea. What you could do is that you create a small hfs+ partition and make the rest ext2 partitions. You would have to do this on linux. Get a ext2 driver for mac [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) and put it on the hfs+ partition and be able to access your ext2 partitons.

I don't know how macintoshes create partitions on external drives. I've only done it on regular ones. But I guess it might do something special that can only be read on mac osx (yet). In that case you'd just have to make regular ones somehow. I'm sorry I can't give you more help.

EDIT: Oh well I guess you can't create hfs+ partitions on linux. You have to do it on osx then.
EDIT2: You should try the command "hpmount" as well

---

### Post by eddie303 on 2006-05-07
The only thing I can say (I own some very old macs here, and I have experimented a bit) that Macs do not treat hard drives like PCs, i.e. the partition table is not in the first sector of the HDD, so that is normal, if you don't see partitions at all in parted/cfdisk. If you run cfdisk on the macintosh itself, it would also give back this, I have tried it on a performa 5200 and MkLinux.

---

### Post by nzmoose on 2006-05-07
thanks guys, ill have a tinker

---

