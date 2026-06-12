---
title: "can I extend my inodes after using it up?"
date: 2010-03-10
forum: Hardware
---

### Post by rabie1 on 2010-03-10
Hi all,

This is my first post in this forum and I hope I can help and get help, too.

I have a problem with the disk space.

```
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             678G  269G  376G  42% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  224K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  140K  1.8G   1% /dev
tmpfs                 1.8G   84K  1.8G   1% /dev/shm
lrm                   1.8G  2.2M  1.8G   1% /lib/modules/2.6.28-18-generic/volatile
```

but my 
```
df -i

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1                44M     44M     13K  100% /
tmpfs                   208K       3    208K    1% /lib/init/rw
varrun                  208K      68    208K    1% /var/run
varlock                 208K       3    208K    1% /var/lock
udev                    208K    1.5K    207K    1% /dev
tmpfs                   208K       2    208K    1% /dev/shm
lrm                     208K      17    208K    1% /lib/modules/2.6.28-18-generic/volatile
```


I still have 58% left but I used all my inodes so practically I don't have any space left. (and also practically, I am screwed)

my question would be:

how do I extend my inodes without having to reformat? and of course, if that is possible.

Best regards, 

Rabie

---

### Post by kidders on 2010-03-11
Hi there,

> **rabie1 said:**
> how do I extend my inodes without having to reformat?I'm afraid you can't. On most filesystem types, the number of inodes is fixed during creation. The "cleanest" solution is to re-create your filesystem from scratch, but you do have other options.

Just a brief note ...

Assuming you've got an Ext3 filesystem created using the default options (*and* assuming I've done my sums right!), the maximum number of files it should be possible for you to create is just shy of 50 million. If you *are* using a default setup, does that seem realistic? If not, it might be worth running fsck, just to be sure your filesystem isn't corrupt.


Anyhow, an alternative to reformatting (which might be impractical if you don't have enough spare time & disk space) is creating another filesystem, and shoving a few million of your tiny files onto it. For example, supposing you're running a mail server, taking /var off your root filesystem could well free up 70 or 80% of your inodes. The required disk space could come from ...[LIST]
[*]**Resizing your root partition.** As things stand, it could be half its current size & you wouldn't notice the difference, so this seems like an obvious choice. Personally, I'm not keen on it though, since you should never resize a partition without doing a full backup first, and you many not have 300G of free disk space lying around.
[*]**A filesystem within a filesystem.** You can create a filesystem pretty much anywhere ... not just on a disk partition (eg /dev/sda2). If you delete one file off your hard disk, you could replace it with one gigantic (eg 50G) file & write a filesystem into it, with a whole new set of inodes. This would let you create lots more files with a minimum of disruption.
[*]**Another disk.** Obviously, another hard disk would be a third option.
[/LIST]

Each of these would be much easier than reformatting, but you might see them as less neat/tidy.

I hope that helps.

---

### Post by srs5694 on 2010-03-11
Moving forward beyond the current crisis (or perhaps taking more time to resolve it), some filesystems don't create a fixed set of inodes at filesystem-creation time. I know that ReiserFS doesn't, for instance, and I believe at least one other Linux filesystem (JFS or Btrfs, perhaps?) doesn't. ReiserFS is also very good about cramming lots of small files together so that they consume less disk space. OTOH, some people say that ReiserFS is less reliable than ext2/3fs, although I personally have never had problems with it. Unfortunately, I know of no easy way to convert from ext2/3fs to ReiserFS, so if you wanted to convert, you'd need to back up, create a new filesystem, and then restore.

Short of switching to ReiserFS, you can change the number of inodes with the -i or -N options to mke2fs, but that will also require backing up, creating a fresh filesystem, and restoring.

---

