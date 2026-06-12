---
title: "Out of space on mostly empty disk."
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by owlcroft on 2009-07-02
When trying to install, via Synaptic, either the latest acroread update or the latest kernel upgrade (to 2.26.27-14), I encounter the dreaded "failed in buffer_write(fd) (10, ret=-1)" error.  I don't know Unix well, and I don't understand where the problem lies, as most of the disk is empty.

Having searched out a few threads, I can offer these data.  First, both regular and Root Trash are empty.  Second, /var has 6.0 GB free: there is nothing big in /var/backups or /var/log.

Next, the output of df -h :

```
df -h

Filesystem            Size  Used Avail Use% Mounted on

/dev/sda5            1012M 1001M     0 100% /
tmpfs                1005M     0 1005M   0% /lib/init/rw
varrun               1005M  332K 1005M   1% /var/run
varlock              1005M  4.0K 1005M   1% /var/lock
udev                 1005M  2.7M 1002M   1% /dev
tmpfs                1005M  616K 1004M   1% /dev/shm
lrm                  1005M  2.4M 1003M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3              96M   26M   66M  28% /boot
/dev/sda9             190G  2.1G  179G   2% /home
/dev/sda8              20G  173M   19G   1% /tmp
/dev/sda7             9.9G  3.2G  6.2G  35% /usr
/dev/sda6             6.8G  478M  6.0G   8% /var

```

Next, the output of du -hc --max-depth=1 (hand-sorted by size):

```
du -hc --max-depth=1

  6.2G	.
  3.1G	./usr
  1.9G	./home
677M    ./media
335M    ./var
246M    ./lib
 26M    ./boot
 14M    ./etc
 12M    ./root
  9.9M  ./sbin
  7.3M  ./bin
  4.4M  ./lib32
  3.3M  ./dev
 80K    ./tmp
 16K    ./lost+found
  4.0K  ./opt
  4.0K  ./srv
  4.0K  ./mnt
  0     ./proc
  0     ./sys
cannot access `./home/eric/.gvfs': Permission denied

  6.2G	total

```

The root partition (apparently sda5) seems 100% full, yet the directories under it are mostly empty.

Can anyone give me some clear, explicit instructions on what I can do here?

Thanks!

---

### Post by merlinus on 2009-07-02
From what I can see, you only gave about 1G for /.  It needs at least 4-5G in order for you to do much of anything.

Post a screenshot of gparted to make sure, and look at possibilities, e.g. using some of the huge space of /home for /.

---

### Post by RJARRRPCGP on 2009-07-02
> **owlcroft said:**
>  I encounter the dreaded "failed in buffer_write(fd) (10, ret=-1)" error.  

That error looks suspicious, likely a bad HDD or a loose HDD connector.

Or a loose USB drive.

---

### Post by owlcroft on 2009-07-02
> **merlinus said:**
> From what I can see, you only gave about 1G for /.  It needs at least 4-5G in order for you to do much of anything.

Post a screenshot of gparted to make sure, and look at possibilities, e.g. using some of the huge space of /home for /.

[IMG]http://owlcroft.com/GParted.png[/IMG]

Considering that there are separate partitions for /var, /user, /home, and /tmp, what would it likely be that eats up so much space in the root?

And, in any event, what--in precise detail for a dummy--ought I best to do about it?

Thanks!

---

### Post by merlinus on 2009-07-03
Why do you need separate partitions for /var, /user, /tmp, and even for /boot?  

The easiest solution is to back up important data and do a fresh install.  Give / 10G, depending on how may apps you intend to install.  1.5G for /swap is plenty, and you can either give all the rest to /home, or create a /data partition as well.

Neither of the last two needs to be formatted upon reinstall or install of a new version, so your data, application configurations and settings, email, and so on will be fine.

Also, I would have one primary partition, in the event that you might need such in future, and then create an extended partition for the rest of the hdd, with logical partitions within that.

---

### Post by owlcroft on 2009-07-03
Is there any alternative to a re-install?

Also, any idea what it is that is eating so much space?

Before installing, I reviewed a great number of articles about how to allocate partition space.  I no longer remember the reasoning--though doubtless I have the texts saved somewhere--but what I eventually used seemed the optimum.  With those separate partitions, the root itself--from what I read--would need only a fraction of 1 GB, but Ubuntu won't install at less than 1 GB for root.

Of course, the Ubuntu habit of retaining all older kernels sopmewhat expands the needed space, but I still am unsure whence the problem.

---

### Post by merlinus on 2009-07-03
The alternative is lots and lots of changes within gparted, and a huge amount of time to do same, because you can only add continguous space to /, and the obvious solution of shrinking /home and adding the freed-up space to / will therefore not work.

You would have to delete and/or move /tmp, /var, and /user before you could do anything that would work long-term.

In future, even after reading articles, how-to's and other people's experiences, a post on the forum serves as a reality check.

Also, if you look in filesystem, you will see many other directories that take up many gigs, e.g. etc, proc, lib, lib32, opt, sys.

---

### Post by owlcroft on 2009-07-03
> **merlinus said:**
> . . . Also, if you look in filesystem, you will see many other directories that take up many gigs, e.g. etc, proc, lib, lib32, opt, sys.
Well, I'm puzzled.  So far as I can see, the directories encompassed in / (that is, which do not have partitions of their own) are:

```

du -hc --max-depth=1   Folder properties in Nautilus

246M	  ./lib      5,912 items, totalling 231.5 MB
677M	  ./media       19 items, totalling  71.1 KB 
 14M	  ./etc
 12M	  ./root
  9.9M	  ./sbin
  7.3M    ./bin
  4.4M    ./lib32
  3.3M    ./dev
 16K	  ./lost+found
  4.0K    ./opt
  4.0K    ./srv
  4.0K    ./mnt
  0	  ./proc
  0	  ./sys

```
And those, between them, sum to something a hair under 1.0 GB, which, I suppose, is why the / partition seems full.

***But*** . . . though when I look with the file browser, the /lib directory is more or less in line with the **du** readout (231.5 MB vs. 246 M), the /media values are wildly diferent: **du** says 677M, whereas clicking the Properties of the /media folder shows contents of 71.1 KB.  That's about 2/3 of a GB that I don't understand.

Also: could I somehow use a symlink to some subdirectory in, say, /home?  Something like symlinking /media to /home/media ?

Being unclear on symlinks, would a symlinked directory *replace* the original (meaning before setting the link I'd have to copy over everything), or does it simply *augment* it?

---

### Post by owlcroft on 2009-07-03
Well, I got it figured out.

The extra 675 MB or so was stashed away in the /media folder: it was a backup thumb memory stick that somehow--as I said, I don't understand Linux very well--apparently had everything from the stick on the hard drive as well, right there in /media/BackUpFolder.  Why clicking on the folder Properties in Nautilus told me that the contents of /media were about 71K I have no idea.  But deleting the subfolder left / at about 335MB--the "a few hundred megabytes" all the partition-size docs had cited--and allowed all the upgrades to proceed smoothly.

I guess I have a lot to learn about using rsync with thumb drives, but for now the system is otherwise just fine.

Thanks, everyone, for the various suggestions.

---

