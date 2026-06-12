---
title: "[SOLVED] Setting up Partitions"
date: 2008-09-10
forum: General Help
---

### Post by Mr.Macdonald on 2008-09-10
I know how to partition and stuff but as i have been reading it seems that i should have a partition setup (/boot /var swap etc.). But how would i do this. I would be booting server edition, so command line please.

would i just zip the contents of /boot, delete /boot contents, mount a drive there and unzip the contents in there, DANGEROUS!!!

I tested, and mounting a drive to a filled folder doesn't copy files into the drive

and where or what is swap, there isn't a /swap so does the system just recognize the swap drive by default???

Feel free to make questions up for me that you think i will be asking, and then answer them :)

Thanks

---

### Post by Vivaldi Gloria on 2008-09-10
1) I suggest you do such important system changes from ubuntu live cd. You can use dd command. Also look at the clonezilla live cd. Depending on what new partitions you make, you may have to change various config files including menu.lst and fstab.

2) There is no reason of having seperate /boot, /var, /usr etc. partitions in a regular system. Only seperate swap and a storage partition(s) (which maybe /home) are enough. What is your justification of having all these extra system partitions? 

3) For swap, use the commands

```
cat /proc/swaps
free -m
```

to see its status. You can use swapon/off commands to start/stop swap usage. See their man pages:

```
man swapon
```

AFAIK, a new swap partition will be automatically used by ubuntu if you add it to fstab.

---

### Post by Mr.Macdonald on 2008-09-10
I am new to the partitioning your system idea and i was wondering why and how you would do it. Many (all) partitioning guides say to do it, you are the only one saying not to ... so explain please because i am clueless

This one especially
[http://ubuntuforums.org/showthread.php?&t=282018]("http://ubuntuforums.org/showthread.php?&t=282018")

---

### Post by Sef on 2008-09-10
I think you are referring to this:

> [SIZE=2]_Advanced partitioning_.[/SIZE]
You can give each system directory a separate mount point. This includes:
/boot
/tmp
/var

This is not needed on a desktop install but is more common in server installs.

Adding /boot, /home, /var, and /tmp partitions can increase security.

For further reading, see References section below.


You are installing a desktop, not a server from my understanding of your thread.   I would start with the 3 basic ones, which is all I use, and I have been using GNU/Linux for many years.    If after gaining experience, you want to add partitions, then go ahead.  But when starting (and sometimes continuing), KISS: Keep It Sweetly Simple.   Much less problems that way.

---

### Post by Mr.Macdonald on 2008-09-10
Yes, all good but how do you implement it. Not how complex or simple, but how do you actually get down and dirty building it?

First Post
> I would be booting server edition

---

### Post by cdtech on 2008-09-10
Do you already have your server setup? Do you want to modify your partitions or is this a new Server install?

---

### Post by Vivaldi Gloria on 2008-09-10
Such detailed partitioning only makes sense in servers and mainframes. In such systems different sytem directories are sometimes on different physical storage devices. **For a regular machine with a single disk, there is no performance gain in making extra /usr, /var etc. partitions.** Actually it makes it harder to maintain for a few reasons. How much space will you allocate for each partition? Also you'll need to allocate some extra empty space on each extra partition to make sure that they don't run out space. All this extra empty space makes storage space smaller. 

So on a regular system only the following partitions make sense:

/
swap
/home or storage partitions
partitions for backup 
partitions for other OS

Sometimes a /boot partition might also make sense but I see no justification for partitions for /etc, /usr, /var, etc in a desktop system. A partition for /var/mail might make sense if you are running a mail server say in a small office environment.

You should also know why there are such system directories to begin with. There are different properties:

>  It is possible to define two independent distinctions among files: shareable vs. unshareable and variable vs. static.

In general, files that differ in either of these respects should be located in different directories. This makes it easy
to store files with different usage characteristics on different filesystems.

"Shareable" files are those that can be stored on one host and used on others. "Unshareable" files are those that
are not shareable. For example, the files in user home directories are shareable whereas device lock files are not.

"Static" files include binaries, libraries, documentation files and other files that do not change without system
administrator intervention. "Variable" files are files that are not static.

For example /etc is an unshareable static directory and /var/mail is a sharable variable directory. So in a multiuser system it might make sense to put a particular kind of directory on another disk for administration, performance, security, space and backup reasons. But in a desktop system there are just a few users So there isn't any gain if you make /etc or /usr partitions. 

The above quote is from Filesystem Hierarchy Standard. To learn more about it click CLI in my sig and scroll down to Part B - 13.

---

### Post by Vivaldi Gloria on 2008-09-10
> **Mr.Macdonald said:**
> This one especially
[http://ubuntuforums.org/showthread.php?&t=282018]("http://ubuntuforums.org/showthread.php?&t=282018")

It says

> Advanced partitioning.
You can give each system directory a separate mount point. This includes:
/boot
/tmp
/var

This is not needed on a desktop install but is more common in server installs.

which is true. 

> but how do you actually get down and dirty building it?

Like I said earlier: 

Ubuntu live cd + gparted + dd command (or clonezilla) + fstab/menu.lst changes

But again, if you don't have any concrete reason of making /tmp, /var etc. don't bother it.

---

### Post by Mr.Macdonald on 2008-09-11
I will be installing server edition, so setup could be before, during or after installation


> Ubuntu live cd + gparted + dd command (or clonezilla) + fstab/menu.lst changes
This means nothing to me. Gparted formats, dd moves/copies binary data. But if I can i use dd on a folder to move its entire contents? when i mount a drive to /boot, all the data that was in /boot will just sit in limbo. If i delete the contents of /boot before mounting, then won't my system lose functionality.

*Apply any directory above as /boot*

See the problems


I am not looking for advice on making the partitions or what i should or shouldn't do.
> There is no reason of having seperate /boot, /var, /usr etc. partitions in a regular system. Only seperate swap and a storage partition(s) (which maybe /home) are enough. What is your justification of having all these extra system partitions?

I just want to know how. Sorry for being frustrated but all your posts have been the same, so if you will be posting something like this
> You should make ... partitions but not these ... and there isn't a performance boost from ... then please just don't reply.

I just want the how not the who what where or when.

Thank you for helping

---

### Post by bingoUV on 2008-09-11
> **Mr.Macdonald said:**
> I will be installing server edition, so setup could be before, during or after installation


During installation, Ubuntu will start a partition editor. Create partitions using this. You can specify mount points for each of the partitions you create. So specify one partition each for /boot, /var and so on.

Post back if you have problems, but it should be simple enough

---

### Post by Vivaldi Gloria on 2008-09-11
> **Mr.Macdonald said:**
> 
I am not looking for advice on making the partitions or what i should or shouldn't do.


Hello? Then why did you ask for it:

> **Mr.Macdonald said:**
> Many (all) partitioning guides say to do it, you are the only one saying not to ... so explain please 

------------------------------


> I will be installing server edition, so setup could be before, during or after installation

You didn't say you'd be installing a new system untill now. My comments about gparted etc were for changing a system. For installing a new one just do what bingoUV says.

---

### Post by Mr.Macdonald on 2008-09-11
thank you

---

