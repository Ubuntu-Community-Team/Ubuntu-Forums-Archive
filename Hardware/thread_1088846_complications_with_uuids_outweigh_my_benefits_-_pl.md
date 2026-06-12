---
title: "complications with uuids outweigh my benefits - please suggest an alternative"
date: 2009-03-06
forum: Hardware
---

### Post by MountainX on 2009-03-06
I'm trying to set up a server with a lot of disks and the mount letters keep changing as I progress through the installation/setup process. So far I have not gotten the system to boot up and successfully mount all disks. Everything works manually when I track down which disk has which ID. 

So now I need a way to keep those disk assignments stable so my scripts will work.

The Ubuntu help docs suggest this:
> Linux now prefers to use [**UUID**]("https://help.ubuntu.com/community/UsingUUID") (Universally Unique Identifier), **LABEL**, or symlinks to identify media storage devices on a system. 

However, after reading up on it, I think UUIDs are not a good solution. In particular, the comments [here]("http://www.linux.com/feature/146951") were really helpful: [http://www.linux.com/feature/146951](http://www.linux.com/feature/146951)
> **"Same here, complications with uuids outweigh my benefits."**So now I need some advice on what to use instead of UUIDs. I like the idea of labels. Will that work when using LVM and encryption?

---

### Post by cariboo on 2009-03-06
UUID's overcome the problems with device labels changing when adding new drives. What is so hard about running:

```
blkid
```

and copying the resulting uuid's into fstab?

Jim

---

### Post by MountainX on 2009-03-06
I guess you didn't read the post I [linked]("http://www.linux.com/feature/146951"). The comments convinced me not to use UUIDs. I'm looking for an alternative and I'm just starting to learn about udev rules or disk-by-label, but I'm not sure if those will work with LVM and crypto.

---

### Post by sdennie on 2009-03-06
Udev rules + disk labels would probably work if you are really adamant about not using UUIDs.  There also already exists /dev/disk/by-id which will have symlinks to your various partitions.  Using udev it should be easy to create a /dev/disk/by-label directory that contains similar symlinks if you are sure you want to go that route.

---

### Post by MountainX on 2009-03-06
> **sdennie said:**
> Udev rules + disk labels would probably work if you are really adamant about not using UUIDs.  There also already exists /dev/disk/by-id which will have symlinks to your various partitions.  Using udev it should be easy to create a /dev/disk/by-label directory that contains similar symlinks if you are sure you want to go that route.
Thank you. I checked and I already have a /dev/disk/by-label directory. I seems to have been created automatically. (Maybe at install time?) The disks I set up manually after install are not linked there, but I will find out if they get added when I give them volume labels.

The reasons given against UUIDs at the link I gave above are all valid for me. As I read through them, I recognized that they represent situations that I face commonly, therefore, I have ruled out UUIDs as a good solution for me.

---

### Post by MountainX on 2009-03-08
What kind of things can I apply a label to? Obviously, I can label a filesystem using e2label or tune2fs.

Can I label partitions that are used as the physical volume for encryption? If so, how?

---

### Post by MountainX on 2009-03-09
I'm still looking for help with this. At this moment, I feel like labels are the right way to go (and that udev rules are too complex for me).

I found [this article that mentions putting labels on partitions]("http://lissot.net/partition/ext2fs/labels.html").

However, I can't seem to get it to work:
```

$ sudo e2label /dev/sdh2 MyLabel
e2label: Bad magic number in super-block while trying to open /dev/sdh2
Couldn't find valid filesystem superblock.
```

/dev/sdh2 is a partition that holds an LVM volume group.

What am I doing wrong?

---

