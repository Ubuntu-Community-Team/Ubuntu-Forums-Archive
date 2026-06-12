---
title: "Partition Delete/Resize Has Caused &quot;Dead Weight&quot;."
date: 2008-07-30
forum: General Help
---

### Post by The Rob on 2008-07-30
Ach! So it was but a month ago that I was new to Linux, but with much fiddling, I found Ubuntu, and tweaked it to perfection. :KS 

However, I then heard how Linux Mint is basically "A better Ubuntu", and so resized my Ubuntu partition to around 45Gb, and used to spare space (around 150Gb) to install Mint.

Long story short, I didn't like Mint as much and deleted the partition, then resized good old Ubuntu's to take up that free space again. But there's a problem: While it says it works, I still only have around 13Gb free (as when it was a smaller partition) and it's labelling some contents as unreadable. I assume the unreadable contents ar ethe 150Gb of deleted partition that I remerged, but I can't figure out how to make them useful again.

I took a long time (and hair-pulling) to get my Ubuntu working just right, I don't want to have to reinstall. Please help!

---

### Post by spiderbatdad on 2008-07-30
Not sure what tool you used to resize your partition. Have you tried the gparted live cd?

---

### Post by The Rob on 2008-07-30
I haven't tried that, but I did use gparted from the Ubuntu live CD...

---

### Post by spiderbatdad on 2008-07-30
just for curiosity sake...
 
what is the output of ```
sudo fdisk -lu
```

and

```
df -h
```

---

### Post by The Rob on 2008-07-30
> **spiderbatdad said:**
> just for curiosity sake...
 
what is the output of ```
sudo fdisk -lu
```

and

```
df -h
```

They would be:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a204a20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476230859   238115398+  83  Linux
/dev/sda2       476230860   488392064     6080602+   5  Extended
/dev/sda5       476230923   488392064     6080571   82  Linux swap / Solaris

```

and 

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              43G   28G   14G  68% /
varrun               1014M  116K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   40K 1014M   1% /dev
devshm               1014M  380K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       43G   28G   14G  68% /home/rob/.gvfs

```

---

### Post by spiderbatdad on 2008-07-30
hmm. obviously conflicting output. Sorry, I'm no expert at this. Fdisk says it's there, df doesnt see it. I would look into the gparted live cd.

---

### Post by unutbu on 2008-07-30
Perhaps try
```

sudo resize2fs /dev/sda1
```

It will either solve the problem or do nothing. Either way, it shouldn't hurt.

---

### Post by spiderbatdad on 2008-07-30
Edited as correction. Apparently resize2fs can be run on a mounted ext3 file system for the purpose of expanding the volume.

---

### Post by The Rob on 2008-07-30
> **unutbu said:**
> Perhaps try
```

sudo resize2fs /dev/sda1
```

If will either solve the problem or do nothing. Either way, it shouldn't hurt.

I did this, and I'm still getting the Some Contents Unreadable error, but there's now 190Gb free. Thanks. :D

Oh, didn't see Spider's latest post. But thanks for you too, as I'm going to still check out the gparted LiveCD. :)

---

### Post by unutbu on 2008-07-30
> **spiderbatdad said:**
> I would be careful throwing out commands like that...resizing partitions requires that they be unmounted, and done in a root shell, or data loss can occur...perhaps linking to a tutorial on that proccess is better than telling someone to run a dangerous command without any better instructions than were provided.:)

Thank you for the word of caution -- I certainly don't want to suggest anything that might cause more harm than good. However, are you sure that this command can not be run on a mounted filesystem, and can you describe under what conditions it is dangerous?

There is nothing in the man page which suggests that this command is dangerous, or even that it can not be run on a mounted filesystem:
```

The resize2fs program will resize ext2 or ext3 file systems.  It can be used  to
enlarge or shrink an unmounted file system located on device.  [B]If the filesystem
is mounted, it can be used to expand the size of the mounted filesystem,  assum&#8208;
ing  the  kernel  supports on-line resizing[/B].  (As of this writing, the Linux 2.6
kernel supports on-line resize for filesystems mounted using ext3 only.).
[B]
If size parameter is not specified, it will default to the size of the partition.[/B]

```

---

### Post by spiderbatdad on 2008-07-30
> **unutbu said:**
> Thank you for the word of caution -- I certainly don't want to suggest anything that might cause more harm than good. However, are you sure that this command can not be run on a mounted filesystem, and can you describe under what conditions it is dangerous?

There is nothing in the man page which suggests that this command is dangerous, or even that it can not be run on a mounted filesystem:
```

The resize2fs program will resize ext2 or ext3 file systems.  It can be used  to
enlarge or shrink an unmounted file system located on device.  [B]If the filesystem
is mounted, it can be used to expand the size of the mounted filesystem,  assum&#8208;
ing  the  kernel  supports on-line resizing[/B].  (As of this writing, the Linux 2.6
kernel supports on-line resize for filesystems mounted using ext3 only.).
[B]
If size parameter is not specified, it will default to the size of the partition.[/B]

```

Hi. I did not mean to accuse you of purposely offering dangerous commands. Everything I have read on resizing partitions says the volume must be unmounted to avoid data loss. Normally a warning will appear if you try to resize a mounted volume, for example with gparted.

There is a link in my previous post that describes using the tool you suggested, and several other guides related to that tool appeared when googled. All suggested umount first.

Because I'm not normally afraid of damaging my installation, I ran the command as you posted. I only got the message "nothing to be done...the volume is max size." Something to that effect. I have used all the space. I was expecting a warning. I'm wondering what would have happened if I had some unallocated space or another partition.

Anyway the concern is generally data loss. If you find information regarding using this tool on a mounted volume, I would like to see it posted.

Edit: I see the man page you quoted refers to expanding a mounted volume...exactly what the OP was looking for. Cheers, and my apologies. Thank you for pointing out my error. I have edited my previous post, as it is irrelevant. The gist is still in the thread through quotes.

Regards.

---

