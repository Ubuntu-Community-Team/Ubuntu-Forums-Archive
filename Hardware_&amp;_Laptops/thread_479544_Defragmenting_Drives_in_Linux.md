---
title: "Defragmenting Drives in Linux?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by OzzyFrank on 2007-06-20
OK, I've read that there is no need to defragment drives in Linux, I've read that is total ********, I've read no defragmenter exists because a big flaw in ext3... you get the idea.

So what's the real story? Could Ubuntu do with a defragmenter, but none exists coz you can't defragment due to ext3 limitations? Does it do it all by itself, or really, truly (magically) not need to? Do tell...

---

### Post by dreadlord_chris on 2007-06-20
> **OzzyFrank said:**
> OK, I've read that there is no need to defragment drives in Linux, I've read that is total ********, I've read no defragmenter exists because a big flaw in ext3... you get the idea.

So what's the real story? Could Ubuntu do with a defragmenter, but none exists coz you can't defragment due to ext3 limitations? Does it do it all by itself, or really, truly (magically) not need to? Do tell...

I haven't found any need to defrag my *nix partitions - **as long as I have >10% free space on the partition**

And where did you read about this "big flaw in ext3"?

---

### Post by stchman on 2007-06-20
> **OzzyFrank said:**
> OK, I've read that there is no need to defragment drives in Linux, I've read that is total ********, I've read no defragmenter exists because a big flaw in ext3... you get the idea.

So what's the real story? Could Ubuntu do with a defragmenter, but none exists coz you can't defragment due to ext3 limitations? Does it do it all by itself, or really, truly (magically) not need to? Do tell...

There is a package in Feisty called defrag.

---

### Post by david_2001 on 2007-06-20
> **OzzyFrank said:**
> So what's the real story? Could Ubuntu do with a defragmenter, but none exists coz you can't defragment due to ext3 limitations? Does it do it all by itself, or really, truly (magically) not need to? Do tell...
Taking the fact that there is no need to defragment as read, ext3 is a journaled filesystem, i.e. it keeps a separate log of disk changes that can be used to recover from a disorderly system shutdown due to a crash or power failure.  Unmounting an ext3 drive and then defragmenting it will destroy the journal.

---

### Post by OzzyFrank on 2007-06-20
Hi. I read about the "flaw" very recently while searching for how to get another ext3 partition to mount r-w at boot in fstab (the answer being to chmod the mount point). I gather the fact the journal can or does get trashed when you defrag is that "flaw". Now, this is if the drive is unmounted? Come to think of it, I didn't know you could do something with a drive unless it was mounted... well, except for being able to partition it still. So if it is mounted, then defragged, is that OK? Is that even possible (ie: theoretically does it need to be unmounted in Linux before a drive can be defragged)? But yeah, read that Linux can actually do with a defragger, that the lack of need for one is a myth, and that ext3 is the hindrance.

---

### Post by dreadlord_chris on 2007-06-20
> **OzzyFrank said:**
>  But yeah, read that Linux can actually do with a defragger, that the lack of need for one is a myth, and that ext3 is the hindrance.

Again I ask - where did you read that?

---

### Post by jrusso2 on 2007-06-20
It is true that you need to remove the journal to defragment ext 3 this makes it ext 2.  But you have not shown there is a need to defragment it.

So far the only file systems I know that need defragmention are used by microsoft.

---

### Post by OzzyFrank on 2007-06-20
"Again I ask - where did you read that?"

If I had the link handy, I would have put it up. When I do a Google search on a subject, I'll fire up dozens of pages, but rarely save links as I will save most of the pages, except for ones that don't really hold any info I think I'll ever need (that page being one of those). And maybe it was searching for "defragmenter ubuntu linux" that I found that, not the search for ext3 mounting info. I suggest looking for "ext3 limitations" or something. It wasn't the only page I came across that basically said ext3 was a big mistake, but this one outlined all the faults or limitations, but I think was trying to be unbiased, and listed other filesystems. Others I saw were having an outright dig at ext3.

"But you have not shown there is a need to defragment it"

I'm not the one making the assertations, actually, just the one who read them. I'm actually here asking you guys since I don't know the answer. I'd still like to know whether defragging is actually unneeded in Linux - ie: the way it managed things means there is no file fragmentation (I mean REALLY, not theoretically) - or if defragging is just not recommended on ext3. Anyway, seems I can't defrag Ubuntu unless I want the journal destroyed, so whether it needs it or not, I won't be doing it till advised otherwise (but I'm still curious to know).

---

### Post by dreadlord_chris on 2007-06-20
> **OzzyFrank said:**
> "Again I ask - where did you read that?"

If I had the link handy, I would have put it up. When I do a Google search on a subject, I'll fire up dozens of pages, but rarely save links as I will save most of the pages, except for ones that don't really hold any info I think I'll ever need (that page being one of those). And maybe it was searching for "defragmenter ubuntu linux" that I found that, not the search for ext3 mounting info. I suggest looking for "ext3 limitations" or something. It wasn't the only page I came across that basically said ext3 was a big mistake, but this one outlined all the faults or limitations, but I think was trying to be unbiased, and listed other filesystems. Others I saw were having an outright dig at ext3.

"But you have not shown there is a need to defragment it"

I'm not the one making the assertations, actually, just the one who read them. I'm actually here asking you guys since I don't know the answer. I'd still like to know whether defragging is actually unneeded in Linux - ie: the way it managed things means there is no file fragmentation (I mean REALLY, not theoretically) - or if defragging is just not recommended on ext3. Anyway, seems I can't defrag Ubuntu unless I want the journal destroyed, so whether it needs it or not, I won't be doing it till advised otherwise (but I'm still curious to know).

as I said before the only time I had anything more then 10% non-contiguous files has been when I've let a partition fill up > 90%

---

### Post by OzzyFrank on 2007-06-20
"the only time I had anything more then 10% non-contiguous files has been when I've let a partition fill up > 90%"

Wow, that's hardly worth worrying about (unless I'm mistaken). Say, how did you find out the info about the amount of fragmentation? Was that using the Linux defrag but telling it not to touch your drive, or something?

---

### Post by yabbadabbadont on 2007-06-20
> **dreadlord_chris said:**
> as I said before the only time I had anything more then 10% non-contiguous files has been when I've let a partition fill up > 90%

Guess again...  ;)
```
/root # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              12G  1.7G  8.8G  17% /
varrun                379M   44K  379M   1% /var/run
varlock               379M  8.0K  379M   1% /var/lock
procbususb            379M  136K  379M   1% /proc/bus/usb
udev                  379M  136K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/hda2             122M   16M  101M  14% /boot
/dev/hda4              31G  5.7G   26G  19% /home
/dev/hda1              32G  2.1G   30G   7% /media/windows
/dev/sda5              45G  877M   44G   2% /media/backup
/dev/sda6              59G   36G   23G  61% /media/music
/dev/sda8              59G  196M   59G   1% /media/projects
/dev/sda9             9.2G  955M  8.3G  11% /media/images
/dev/sda7              60G   42G   19G  70% /media/video
/root # umount /media/music 
/root # fsck -f /dev/sda6
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Music: 1720/7815168 files (44.0% non-contiguous), 9623366/15627220 blocks
/root # grep music /etc/fstab
UUID=2eacc7c6-729a-46a8-a6f9-8cd1b148a411 /media/music     ext3    defaults        0       2

```

---

### Post by steveneddy on 2007-06-20
OK - I give. 

What's 

```
df
```

?

---

### Post by yabbadabbadont on 2007-06-20
> **steveneddy said:**
> OK - I give. 

What's 

```
df
```

?

RTFM...    :twisted:

OK, just kidding.  Run, "man df", in a terminal window.

Alright, alright.  No need to ban me.  It means "disk free".  :D

---

### Post by steveneddy on 2007-06-20
> **yabbadabbadont said:**
> RTFM...    :twisted:

OK, just kidding.  Run, "man df", in a terminal window.

Alright, alright.  No need to ban me.  It means "disk free".  :D

I did man df and I still was confused.

Gee - you are so smart!

will you do my homework?

---

### Post by yabbadabbadont on 2007-06-20
> **steveneddy said:**
> Gee - you are so smart!

will you do my homework?

I would if we weren't about the same age....  I doubt that you have homework.  (unless you are changing careers)  :D

---

### Post by atlfalcons866 on 2007-06-20
[http://ubuntuforums.org/showthread.php?t=169551&highlight=pyfrag](http://ubuntuforums.org/showthread.php?t=169551&highlight=pyfrag)

---

### Post by dreadlord_chris on 2007-06-20
> **yabbadabbadont said:**
> Guess again...  ;)
```
/root # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              12G  1.7G  8.8G  17% /
varrun                379M   44K  379M   1% /var/run
varlock               379M  8.0K  379M   1% /var/lock
procbususb            379M  136K  379M   1% /proc/bus/usb
udev                  379M  136K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/hda2             122M   16M  101M  14% /boot
/dev/hda4              31G  5.7G   26G  19% /home
/dev/hda1              32G  2.1G   30G   7% /media/windows
/dev/sda5              45G  877M   44G   2% /media/backup
/dev/sda6              59G   36G   23G  61% /media/music
/dev/sda8              59G  196M   59G   1% /media/projects
/dev/sda9             9.2G  955M  8.3G  11% /media/images
/dev/sda7              60G   42G   19G  70% /media/video
/root # umount /media/music 
/root # fsck -f /dev/sda6
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Music: 1720/7815168 files (44.0% non-contiguous), 9623366/15627220 blocks
/root # grep music /etc/fstab
UUID=2eacc7c6-729a-46a8-a6f9-8cd1b148a411 /media/music     ext3    defaults        0       2

```

hmmm...
```

chris@HAL421:~$ sudo df -h
Password:
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              12G  2.1G  9.2G  18% /
varrun                506M  140K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
procbususb            506M  108K  506M   1% /proc/bus/usb
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   23M  484M   5% /lib/modules/2.6.20-16-generic/volatile
/dev/hdd4             9.7G  6.6G  2.7G  72% /usr
/dev/hdd3             9.7G  4.1G  5.1G  45% /home
/dev/hda1              62G   14G   46G  24% /media/DriveA
/dev/hdd1              53G   21G   31G  40% /media/DriveB
/dev/hdb1             233G  113G  120G  49% /media/DriveC
chris@HAL421:~$ sudo umount /media/DriveB
chris@HAL421:~$ sudo fsck -f /dev/hdd1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
System: 13814/6963200 files (7.1% non-contiguous), 5496297/13898225 blocks
chris@HAL421:~$ grep DriveB /etc/fstab
UUID=45eb76ed-6043-41ab-a272-6776dd6f1713 /media/DriveB ext3 defaults,data=writeback 0 2

```
should I keep guessing?

---

### Post by yabbadabbadont on 2007-06-20
> **dreadlord_chris said:**
> hmmm...
should I keep guessing?

Geeze, you would think that I hadn't included a smiley with my post.  :D

However, I guess it wasn't clear that I wasn't disputing that *you* have never seen such fragmentation, just that it does happen.  Actually, since you read my post, you **have** seen such fragmentation now.  ;)

---

### Post by dreadlord_chris on 2007-06-21
> **yabbadabbadont said:**
> Geeze, you would think that I hadn't included a smiley with my post.  :D

However, I guess it wasn't clear that I wasn't disputing that *you* have never seen such fragmentation, just that it does happen.  Actually, since you read my post, you **have** seen such fragmentation now.  ;)

I wasn't taking offense - maybe I should have included a smiley ;)

---

### Post by tgalati4 on 2007-06-21
There are two times in Linux when defragmentation occurs.

1.  Installing a Linux distro
2.  Reinstalling a Linux distro.

If fsck ever shows greater than a few percent of non-contiguous files AND your disk is not full, then you probably have other problems that need fixing and it's time for a new distro anyway.

Linux is not Windows so thinking with a Windows mentality will trip you up.

Enjoy it and be happy.  Disk fragmentation will take care of itself.

---

### Post by mfichifichi on 2007-06-21
The wikipedia entry for [ext3]("http://en.wikipedia.org/wiki/Ext3") attempts to explain:
> There is no online ext3 defragmentation tool working on the filesystem level. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first. But depending on the feature bits turned on on the filesystem, e2defrag may destroy data; it does not know how to treat many of the newer ext3 features.[4]

There are userspace defragmentation tools like Shake[2] and defrag[3], which work by copying each file and hoping the newly allocated file was not fragmented. However this only works if the filesystem is reasonably empty, and such filesystems are not usually fragmented. A true defragmentation tool does not exist for ext3 [4].



---

### Post by david_2001 on 2007-06-21
> **OzzyFrank said:**
> Hi. I read about the "flaw" very recently while searching for how to get another ext3 partition to mount r-w at boot in fstab (the answer being to chmod the mount point). I gather the fact the journal can or does get trashed when you defrag is that "flaw". Now, this is if the drive is unmounted? Come to think of it, I didn't know you could do something with a drive unless it was mounted... well, except for being able to partition it still. So if it is mounted, then defragged, is that OK? Is that even possible (ie: theoretically does it need to be unmounted in Linux before a drive can be defragged)? But yeah, read that Linux can actually do with a defragger, that the lack of need for one is a myth, and that ext3 is the hindrance.
Having a journal is not a flaw, it's a feature.  In the meantime, defragmenting a mounted drive, even if there were a program that did this, would risk data integrity.  The defragmentation program would have to be able to cope with the situation where a file being moved/consolidated was simultaneously written to by a user or program.

---

### Post by OzzyFrank on 2007-06-25
> **tgalati4 said:**
> ...it's time for a new distro anyway.

So what happens if you're one of the weirdos who doesn't just install another distro whenever a problem is encountered in the current one? I mean, to ditch an operating system coz of fragmentation issues seems a bit extreme... and in the context of this thread means the best advice for me as an Ubuntu user who encounters a high rate of fragmentation is to ditch Ubuntu for another flavour of Linux? So what happens if I have better things to do with my time than install distros, and actually like Ubuntu and want tostick with that?

Anyway, this thread has been informative, as it is obvious that the jury is out on whether fragmentation is a factor in Linux (or Ubuntu anyway). Seems maybe ext3 could do with a defragmenter, but I won't be using the experimental one that guy in the other thread is testing on people's machines, hehe.

---

### Post by yabbadabbadont on 2007-06-25
The classical solution to fragmentation in Unix/Linux systems is to backup the fragmented filesystem, recreate it, and restore from backup.  I'm not too worried about it as it is (in my case) just music and doesn't cause any problems during playback.

---

### Post by Quintin Riis on 2007-06-25
> **OzzyFrank said:**
> Anyway, this thread has been informative, as it is obvious that the jury is out on whether fragmentation is a factor in Linux (or Ubuntu anyway). Seems maybe ext3 could do with a defragmenter, but I won't be using the experimental one that guy in the other thread is testing on people's machines, hehe.
"the jury" is not "out".  The answer is it generally doesn't matter one way or the other if a filesystem is fragmented or not.

This is the first question we've answered in a new service my company is experimenting with.  You can check it out and comment at the following link:

[http://daecom.biz/ask/2007/06/25/how-do-i-defragment-my-hard-drive-in-linux/#more-8](http://daecom.biz/ask/2007/06/25/how-do-i-defragment-my-hard-drive-in-linux/#more-8)

---

