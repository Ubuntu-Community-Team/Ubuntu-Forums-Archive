---
title: "Size of Ubuntu Install?"
date: 2008-08-02
forum: General Help
---

### Post by nisden on 2008-08-02
I bought a new laptop and i am going to make it Dual boot, now i am just trying to figure out how i should format the hardrive, i am thinking about splitting it up in 3 parts.

10gb ext3 (For Ubuntu)
10gb ntfs (For Windows Thinking about Vista :S)
180gb fat32 (For file storage)

Does this seem like a good idea or any one that got a better idea:confused:

---

### Post by tamoneya on 2008-08-02
as far as ubuntu goes it looks fine.  Just remember you also need a swap partition of a couple of gigs.  Vista however is different problem.  You definitely want at least 20 or 30 GB for vista.  I personally would use more.

---

### Post by coffeecat on 2008-08-02
> **nisden said:**
> 180gb fat32 (For file storage)

Why not make this NTFS now that NTFS read-write is reliable in Ubuntu with the ntfs-3g driver? NTFS is more robust than fat32 and doesn't have the 4Gb filesize limitation of fat32. The installer will set up fstab so that it will be mounted on bootup if you want.

I agree with tamoneya about needing more than 10Gb for Vista. XP will soon use up 10Gb if you install more than a few apps on it, and Vista is much more resource hungry.

---

### Post by speedkreature on 2008-08-02
I am in agreeance with tamoneya, you'll want at *least* 30GB for Vista.

Is there a particular reason you want a separate partition for file storage.  Ubuntu does a great job reading and writing NTFS and there's a wonderful [driver ]("http://www.fs-driver.org/")for ext2/3 in Windows (I make use of the latter daily as all of my flash drives are ext2).

With the former option (large NTFS partition) you find it's easier to manage your files in Vista and allows for OS bloating (just extra space for all those files and programs that get installed over time).  With the latter, you'll probably find yourself gradually moving away from Windows (at leas that's what happened to me).

But that's just my 2 cents.

---

### Post by knutschr on 2008-08-02
I have Ubuntu, Medibuntu and Kubuntu installed.
I use 16 GB by now apart from my /home.
I have a lot installed though..

---

### Post by nisden on 2008-08-02
Okay new setup is then.

10gb ext3 (ubuntu)
30gb ntsf (Windows Vista)
160gb ntsf

The intention is that i am going to do so Windows vista install every thing else then the Operation system on the 160gb ntfs. I am going to try and do the same with ubuntu (that is porbaly going to be my second question)

---

### Post by bobbob1016 on 2008-08-02
I wouldn't say to pick NTFS.  Even though it can be read and written, if you have to shut down Windows with the power button (hard shutdown) NTFS-3G can have issues starting read/writing again.  If you don't think you're going to be using files over 4gig, use FAT32, or maybe make a 20gig NTFS partition for files over 4gig, so you don't have to reboot into Windows to get your NTFS properly unmounted.  Also, I'd suggest making /home and / a seperate partition, /bin and /usr/bin wouldn't hurt either, so if you need to reinstall, everything is still there.

---

### Post by RATM_Owns on 2008-08-02
What about ext2?
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by nisden on 2008-08-02
Mainly because i want to keep it a bit simple :D

---

### Post by nisden on 2008-08-02
Okay i thought a bit about this now and i have come to this idea.

170gb ext3 for Ubuntu and Windows Programs Using the ext driver :D
30gb ntfs for windows :D

Any one got some input on that :confused:

---

### Post by coffeecat on 2008-08-02
> **bobbob1016 said:**
> I wouldn't say to pick NTFS.  Even though it can be read and written, if you have to shut down Windows with the power button (hard shutdown) NTFS-3G can have issues starting read/writing again.

That's not logical. If you had to do a hard shutdown with Windows while it was writing to a fat32 partition, you could get data corruption on the fat32 partition such that it is unrepairable and possibly unreadable. Not only could you; many people have. NTFS is a journalled filesystem, so even if you get read-write problems after a hard shutdown, Windows can (usually) repair the filesystem. In the scenario you describe NTFS is likely to be **more** robust, not less.

---

### Post by bobbob1016 on 2008-08-03
That could be an issue, since it is POSSIBLE, not likely, but possible that a Windows virus could mess with your Linux partition.  It'd have to be aware that Linux was there to infect it, but it could overwrite files or something.  I think you should keep the data on a different ext3 partition, and encrypt your / and /home, or put your / and /home on ext3 and your shared as ext2, and just install the ext2 driver in Windows.

---

### Post by Vishal Agarwal on 2008-08-03
For my laptop, what I did is,

1. One primary partition 20GB for windows XP
2. Extended partition 20GB for D Drive
3. Extended Partation 2GB for SWAP (For 1GB RAM)
4. Extended Partition 15GB for Ubuntu root (/)

Balance is unpartitioned space, which I will utilize later as per requirement.

First I installed the windows XP then I installed the UBUNTU. The GRUB boot loader is installed in primary partition, And all the Dual boot etc. are working fine.

---

### Post by Vishal Agarwal on 2008-08-03
Also the windows FS I choose is WIN32, not NTFS.

---

