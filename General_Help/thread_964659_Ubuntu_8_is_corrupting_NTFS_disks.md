---
title: "Ubuntu 8 is corrupting NTFS disks"
date: 2008-10-31
forum: General Help
---

### Post by OscarWabbit on 2008-10-31
Hi

I have a very strange and worrying problem.  Let me explain.

I have a windows vista machine and an ubuntu machine. For several months I have been using NTFS on all disks so that both Ubuntu and Vista can share disks, without any problems.

Since a couple of days ago it seems like Ubuntu is corrupting any ntfs disk I attach to it.

What is specifically happening is this.

When I attach a newly formatted NTFS disk to my ubuntu machine and copy files to the disk, everything works fine in Ubuntu.  When I then cleanly unmount the volume and reconnect the disk drive to my windows machine, Windows can not see the partition.  When I re-attach the disk to ubuntu, ubuntu can read the volume.

So in ubuntu the disk is readable but in windows it is not.

This has happened on 3 different disks in the last couple of days.  I did a brand new installation of Vista yesterday but the problem has happened again today.

When I run "chkdsk n:" where n: is the NTFS disk which is unreadable in windows, it comes up with alsorts of errors.

The chkdsk errors read:

"An index entry from index $0 of file 25 is incorrect"

I have not yet tried "chkdsk /r" to try and recover the disk on windows - that is my next job (I'm just backing up the currently corrupted disk on ubuntu to another disk to make sure I dont lose the data).

What baffles me about this problem is that it has only started in the last few days and nothing has changed on either my windows or ubuntu system.

This has happened now to 3 different disks all different makes and sizes (one Lacie disk, one toshiba and one Western Digital).

It seems like Ubuntu is in some way corrupting the disks so that they are unreadable in Windows Vista but still remain readable in Ubuntu.

Any help would be appreciated.


PS I have tried ntfsfix and that didnt resolve the problem.

Thanks

---

### Post by ju2wheels on 2008-10-31
If you mean you ran ntfsfix on Ubuntu, I dont think that makes much of a difference, as it doesnt actually fix the ntfs partition table at all, it just marks it as needed to be scanned so that it gets check disked when Windows next boots up.

Out of curiosity, which version of ntfs-3g do you have installed?

```

ntfs-3g --help

```

---

### Post by OscarWabbit on 2008-10-31
> **ju2wheels said:**
> If you mean you ran ntfsfix on Ubuntu, I dont think that makes much of a difference, as it doesnt actually fix the ntfs partition table at all, it just marks it as needed to be scanned so that it gets check disked when Windows next boots up.

Out of curiosity, which version of ntfs-3g do you have installed?

```

ntfs-3g --help

```


Hi

The version of ntfs-3g is:

1.2216 Fuse 27

Cheers
Oscar

---

### Post by ju2wheels on 2008-10-31
The latest is currently 1.2506 (on intrepid) and 1.5 bleeding from their site, I would recommend upgrading and it should solve your problem. Older ntfs-3g are known to have problems as the one you describe.

I assume you are still running 8.04 since the newer 1.2506 version is already included in 8.10. 

I would recommend install the bleeding edge version since you are using Vista with this partition a lot and in addition to this, I would not use Vista to format these drives to NTFS but instead use GParted (Partition Editor) on Ubuntu. The reason I suggest not formatting in Vista is in case it creates a newer version of the NTFS file system that may cause issues with the Linux ntfs-3g module (just a theory there but I wouldnt be surprised if M$ does some weird stuff with it in Vista).

So that said try the following:
```

wget http://www.ntfs-3g.org/ntfs-3g-1.5012.tgz
tar xvfz ntfs*
cd ntfs-3g-1.5012/
./configure
make
sudo make install
ntfs-3g --help

```

Ok so here just make sure you have build-essential installed already and you should have no problems. If anything most of your problems will come in the first step during configuration due to missing packages but we can sort that out quickly if any. At the end just confirm ntfs-3g is the new version and continue with your backup/repair of drives and hopefully it shouldnt happen again.

---

### Post by OscarWabbit on 2008-10-31
> **ju2wheels said:**
> The latest is currently 1.2506 (on intrepid) and 1.5 bleeding from their site, I would recommend upgrading and it should solve your problem. Older ntfs-3g are known to have problems as the one you describe.

I assume you are still running 8.04 since the newer 1.2506 version is already included in 8.10. 

I would recommend install the bleeding edge version since you are using Vista with this partition a lot and in addition to this, I would not use Vista to format these drives to NTFS but instead use GParted (Partition Editor) on Ubuntu. The reason I suggest not formatting in Vista is in case it creates a newer version of the NTFS file system that may cause issues with the Linux ntfs-3g module (just a theory there but I wouldnt be surprised if M$ does some weird stuff with it in Vista).

So that said try the following:
```

wget http://www.ntfs-3g.org/ntfs-3g-1.5012.tgz
tar xvfz ntfs*
cd ntfs-3g-1.5012/
./configure
make
sudo make install
ntfs-3g --help

```

Ok so here just make sure you have build-essential installed already and you should have no problems. If anything most of your problems will come in the first step during configuration due to missing packages but we can sort that out quickly if any. At the end just confirm ntfs-3g is the new version and continue with your backup/repair of drives and hopefully it shouldnt happen again.



Hi ju2

Many thanks for this help.  Your assistance is most appreciated.

I have followed your instructions and the compilation and installation of the latest ntfs-3g went fine, without a hitch and ntfs-3g --help confirms the latest version is now installed.

I have noted what you said about creating ntfs partitions using gparted and that makes a great deal of sense, and is something I hadn't thought of before - I've always initialised new disks by formatting them ntfs on my windows server first.  From now on, I will do this on ubuntu.

I'll now cross my fingers and toes and hope the problem is resolved.

Again, thank you.
Oscar

---

### Post by szaka on 2008-11-01
The chkdsk message is harmless and 100% unrelated to Ubuntu: [http://ntfs-3g.org/support.html#indexo](http://ntfs-3g.org/support.html#indexo)

There isn't any evidence your NTFS would be corrupted. The issue here is that Windows can not access it for some reason. The two problems are absolutely not the same. Your problem sounds more like this: [http://ntfs-3g.org/support.html#mbr](http://ntfs-3g.org/support.html#mbr)

---

### Post by OscarWabbit on 2008-12-29
> **ju2wheels said:**
> The latest is currently 1.2506 (on intrepid) and 1.5 bleeding from their site, I would recommend upgrading and it should solve your problem. Older ntfs-3g are known to have problems as the one you describe.

I assume you are still running 8.04 since the newer 1.2506 version is already included in 8.10. 

I would recommend install the bleeding edge version since you are using Vista with this partition a lot and in addition to this, I would not use Vista to format these drives to NTFS but instead use GParted (Partition Editor) on Ubuntu. The reason I suggest not formatting in Vista is in case it creates a newer version of the NTFS file system that may cause issues with the Linux ntfs-3g module (just a theory there but I wouldnt be surprised if M$ does some weird stuff with it in Vista).

So that said try the following:
```

wget http://www.ntfs-3g.org/ntfs-3g-1.5012.tgz
tar xvfz ntfs*
cd ntfs-3g-1.5012/
./configure
make
sudo make install
ntfs-3g --help

```

Ok so here just make sure you have build-essential installed already and you should have no problems. If anything most of your problems will come in the first step during configuration due to missing packages but we can sort that out quickly if any. At the end just confirm ntfs-3g is the new version and continue with your backup/repair of drives and hopefully it shouldnt happen again.



Just as a reference for anyone reading this thread with the same problem.  The solution offered here by ju2wheels has fixed the problem.  Since upgrading to the latest version of ntfs-3g using the instructions above, I have had no further disk problems.

Thanks ju2.

Oscar

---

