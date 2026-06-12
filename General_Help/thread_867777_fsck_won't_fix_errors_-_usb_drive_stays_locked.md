---
title: "fsck won't fix errors - usb drive stays locked"
date: 2008-07-23
forum: General Help
---

### Post by souldances on 2008-07-23
my 'my book' usb drive is locked as read-only apparently due to a bunch of filesystem panic errors.  i've tried fixing these with fsck, with drive mounted and unmounted.  after having me go through a bazillion fix/don't fix replies, it says its left the filesystem unchanged and nothing is fixed.  HELP - how do i fix the errors on the drive?  it's got 350gb of free space that i can't access and i don't want to lose the 150gb of data that's there.  
i'm using ubuntu gutsy.

---

### Post by danwood76 on 2008-07-23
Can you give a bit more info about the drive?
For example what format it is etc?

Im assuming its EXT3 if your using fsck.
You need to make sure the drive isnt mounted when running fsck or it wont repair errors.
Its also possible to automatically answer yes to all the fixing questions with:

```

sudo fsck /dev/DRIVE_BLOCK_ID -y

```

---

### Post by McLogic on 2008-08-06
If you are worried about data loss, the best thing to do is copy the 150 gigs to a different hard drive. You could then either repair or reformat the drive. I have also had problems like this.

I fixed the file system by booting into Microsoft Windows. If you don't have that option, or do not want to. Try these commands.

/sbin/fsck.vfat -a /dev/hda5
[http://linux.die.net/man/8/fsck.vfat](http://linux.die.net/man/8/fsck.vfat)

or (ends up using the same program)

dosfsck [-aAflrtvVwy] [-d path -d ...]  [-u path -u ...]  device
[http://www.linuxcommand.org/man_pages/dosfsck8.html](http://www.linuxcommand.org/man_pages/dosfsck8.html)

This command is from this forum post:
[http://www.linuxquestions.org/questions/linux-general-1/mounted-read-write-fat32-partition-suddenly-becomes-read-only-166190/](http://www.linuxquestions.org/questions/linux-general-1/mounted-read-write-fat32-partition-suddenly-becomes-read-only-166190/)

---

### Post by Herman on 2008-08-07
Try out e2fsck instead of just plain fsck.
e2fsck is good for ext2 or ext3 file systems.
fsck actually runs e2fsck but without the full range of options. We are better off running e2fsck ourselves directly instead of through fsck. 
Here's a link with some commands that might help you, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD.

---

