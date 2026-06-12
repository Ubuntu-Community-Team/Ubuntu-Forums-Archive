---
title: "Dividing a partition"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by andreasDK on 2005-04-07
How do I go about creating some partitions on a 120GB Hoary machine?

The OS is functioning beautifully but i need some backup drives and want to limit Hoary to something like 25GB or so dividing the rest between the two backups.

Is this possible?
Please help me.

---

### Post by az on 2005-04-07
Offhand, I do not know what partitioning tools are included in hoary, but the installer can split partitions for you.

You need to unmount the drives anyway, so Either boot from another disk, or use a live cd and work from a ramdisk - Like The live cd or the installer!

Just boot as usual, and make your way to the partitionner, pick manual partitioning and select the partition you want to split.

Change it's size and make it go.  You will now have some free space.

Then you can make a filesystem on that free space.  If this changes the naming of your current partition, make sure to modify your fstab to change the / device.

If ubuntu is the only OS on your drive and you are making space after Ubuntu, don't worry.

Do not continue the install procedure after you finished partitioning, just reboot.

---

### Post by maqi on 2005-04-07
You can also try gparted. It's kind of like Partition Magic. It's a visual tool and you can do your partitioning from your desktop environment - though you may need to reboot before changes take effect. I have used it with success, and it's much easier - and therefore probably safer - than using the install disk partitioning tool.

Just enable the Universe repositories and then do
```
$ sudo apt-get update
$ sudo apt-get install gparted
```

Enjoy :)

maqi

---

### Post by andreasDK on 2005-04-07
Hi again.

Thanks for the replies.

I have now installed gparted but have discovered that I cannot do much from there hence basicly all options, including Partition, are greyed out.
This is naturally because I am using the disk as we speak.
Is there a work-around for this?

Alternatively I am willing to boot from a live-cd that contains gparted but I would really prefer not having to reinstall. The PC is set just the way i want and a lot of work is floating around.

---

### Post by maqi on 2005-04-07
Doh! I didn't think of that #-o

Well the live CD is an option but ubuntu doesn't contain gparted as a default program :(

Unless  you want to spend your time finding and then downloading a live distro with a graphical partitioner I suspect that azz's suggestion about using the installation partitioner is going to be your quickest option. 

It will be safe too. I just like to "see" what I'm doing so if possible I prefer to use gparted - but if you follow azz's instructions you should be fine :)

cheers,
maqi

---

### Post by andreasDK on 2005-04-07
Will do...

---

### Post by Winterfresh on 2005-04-08
I've had good partitioning experiences with qtparted, which comes on the [Knoppix](http://www.knoppix.org/) live CD. Even managed to partition one large NTFS partition (with Windows XP on it) into four smaller partitions (one NTFS, one FAT32, one ReiserFS for Linux, and one Linux swap). Windows didn't even notice!   :wink: 

(But be sure to back up your data first if you try this, and always defrag before you partition a drive with valuable data on it.)

---

