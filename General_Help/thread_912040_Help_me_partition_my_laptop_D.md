---
title: "Help me partition my laptop :D"
date: 2008-09-06
forum: General Help
---

### Post by wersdaluv on 2008-09-06
I just bought a Fujitsu Esprimo Mobile U9200. It's fresh without an OS. I'm planning to install, of course, Ubuntu on it. It has a 160gb hard drive.


I'm thinking of having five partitions. One for my /home partition, one for my main Ubuntu partition, one for Windows XP, one for my super light ubuntu distro (maybe PUD Linux for quick boots), and one for swap. Is that feasible? Is it a good idea? How do I pattern my partitions (meaning, which should come first)?

Also, if I change my mind one day and decide that I don't need one of the operating systems anymore (maybe the super light OS), will I not have a problem with deleting and adjusting partitions? Is that a safe thing to do?

---

### Post by Scunge on 2008-09-06
All I can suggest is what works for me.

First install Windows XP and, during it's partitioning stage, create a single primary NTFS partition at the start of the disk. I used a partition of size 12288 MB (= 12 GiB) since most of my apps are running in Ubuntu; XP may round that up a bit depending on disk make-up. Install XP in that.

Up to you whether you do all the Windows Updates and application installs now or later. You might also like to reflect to some extent in Windows what is done by most people in Ubuntu; separate out your data. So use the Windows Computer Management tool to create the partition layout.

In my case, I have:
- a second unformatted primary partition of 16GB for Ubuntu "/";
- a third primary partition, also 16GB, for your super-light system;
- an extended partition, in which I create my 32GB Windows "Data" NTFS partition, labelled "D:", and move "My Documents" onto it; Ubuntu's stuff will come later.

Those sizes are just my example; depends on what you use your computer for how you'll end up sizing things.

Now, insert the Ubuntu alternate CD and reboot. Select the option to manually edit the partition table.

Here I set up the primary partition for Ubuntu I created earlier, and the swap and data partitions.

This is the actual setup I have on my dual-boot Ubuntu and Windows machine. Notice that what I enter as 16GB in Windows comes out as 17.2GB here; I think that's unformatted size whereas the Windows setup takes formatted size.

```

#1 primary  12.9 GB   K ntfs  /media/hda1 - This is Windows "C:"
#2 primary  17.2 GB B F ext3  /
#3 primary  17.2 GB     unformatted - your super-light version goes here
#5 logical  34.4 GB   K ntfs  /media/hda5 - This is Windows "D:"
#6 logical   1.0 GB   f swap  swap
#7 logical <remain>   f ext3  /home

```

If you wanted a "/home" for your super-light installation as well, just split up the <remain> into two as you like.

Once Ubuntu's installed and updated, the only thing left I need to do is make the Windows partitions available in Ubuntu, but I don't want them in "/media" because I want to just exclude "/media" in my backup setup; it's easier therefore to put things I *do* want backed up outside of "/media".

This is what I do:
```
$ cd /
$ sudo mkdir WindowsXP
$ sudo chmod 555 WindowsXP
$ cd WindowsXP
$ sudo mkdir System
$ sudo mkdir Data
$ sudo chmod 550 *
$ sudo vi /etc/fstab:
- Add at end:
  - # Local Partitions - Windows XP
    /dev/hda1 /WindowsXP/System		ntfs	defaults,nls=utf8,umask=007,gid=46 0 1
    /dev/hda5 /WindowsXP/Data		ntfs	defaults,nls=utf8,umask=007,gid=46 0 1
- Remove any existing lines for those partitions

```

If you wanted Desktop icons, then you would do something like this:
```
$ cd ~/Desktop
$ ln -s /WindowsXP/System "WinXP System"
$ ln -s /WindowsXP/Data "WinXP Data"

```

And as I said, that works for me.

Now, for your super-light Ubuntu, I am guessing it would be repeat the second part above, but put it into that unformatted third primary partition. You can use the same swap partition, that's no problem.

---

### Post by Universal344 on 2008-09-06
EDIT: Use above, instructions are better.

You've got quite the task set out for you.  There are a couple ways to do this but I would suggest the following.  First, run the XP installer.  When it gets to the partitioner, create a C partition (if hasn't already done it for you).  Keep in mind disk space as you do this.  After that has run and you have XP configured, install Ubuntu (you'll need an ISO recording tool to do this).  When the Ubuntu installer comes to the partitioner, create a main Ubuntu partition (ext3)and a swap partition.  Then go ahead and let it install.  I do not know about the installation process for super light Ubuntu, but you would install that next.  NOTE: a disk can only have 5 partitions so you will have to deny Super Light Ubuntu swap.  I don't know what you need a /home partition for, but if you really need it you can grab gParted from add/remove programs in Ubuntu and use that to create a /home partition provided you have enough space on your drive.  I would not do any of this until some one else confirms it.  Hope this was helpful!

---

### Post by Scunge on 2008-09-06
> **Universal344 said:**
> NOTE: a disk can only have 5 partitions so you will have to deny Super Light Ubuntu swap.  I don't know what you need a /home partition for, but if you really need it you can grab gParted from add/remove programs in Ubuntu and use that to create a /home partition provided you have enough space on your drive.
As far as I understand it, a disk can have (up to) only 4 partitions, either all primary, or one primary replaced by an "extended" partition. Into that, though, you can put as many "logical" partitions as you like, well, there is a limit, but it's alot.

In any case, you can certainly reuse the "full" Ubuntu swap partition for the super-light installation without problems, you won't be able to run them both simultaneously, and by definition it's temporary data.

As for why you need "/home", I'm sure there are lots of threads out there discussing this, but the main reasons I am aware of are that:
- you can limit your system partition size independently from how much data space you need;
- similarly, you can fill up your data partition and know that your system at least still has space to run;
- you can reinstall your system (i.e. format the system partition) without ending up wiping your data as well;
- you can backup, or transfer, data partitions independently of the system

and I'm sure there are other reasons.

Some people go further and create separate partitions for "/boot" and some of the other root directories, for pretty much the same reasons.

---

### Post by Bucky Ball on 2008-09-06
Windoze needs a primary partition at the beginning of the drive (I would make that during the Windoze install and leave the rest free space). Yes, you can only have 4 partitions of any kind but with extended partitions, you can have many logical partitions inside that (many more than 4). Linux doesn't need a primary partitions, logical is fine.

So, you could have your primary partition at the beginning of the drive, make an extended partition with the rest and put your Ubuntu install and its partions inside that (no need to set them as primary, just make sure you set the Linux partition to boot and include a swap twice the size of you RAM).

\\:D/

ps: it is important to install windoze on the first partition - you will run in to all kinds of headaches if you don't and wind up doing so anyhow. You know MS, always gotta be numero uno, in this case literally.

---

### Post by wersdaluv on 2008-09-06
Thanks, guys. Done partitioning :)

---

