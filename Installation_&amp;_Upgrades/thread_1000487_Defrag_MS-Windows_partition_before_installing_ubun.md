---
title: "Defrag MS-Windows partition before installing ubuntu??"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by Halo_gg on 2008-12-02
Hi all,

Just about to install ubuntu on my recently purchased IBM T60 laptop (!), so I am trying to be cautious here not to break things before I set myself comfortably (hopefully) in a Linux environment.

Back to the story, the laptop has already had Windows Vista on it on C drive (old windows language...) and I had D drive setup for data/file. So I am planning to use the rest of the 100GB hdd space to install ubuntu. I read a thread for opensuse installation and a BIG point there is to "MS-Windows Users - you MUST defrag" - the reason being if you have not already prepared a partition for openSUSE, then openSUSE installer will try to carve up your MS-Windows hard drive (allocating space for both MS-Windows and Linux), and a badly fragmented drive can cause problems.

Is this applicable for ubuntu installation as well?

Thanks,
Halo_gg

---

### Post by lisati on 2008-12-03
It's always a good idea to defrag Windows partitions every now and then, even if you're not installing another OS - it helps to keep all parts of a file together (which helps efficiency accessing files), and usually moves data towards the "start" of the partition. You might also consider cleaning out temporary files from Windows too - there are a number of utilities available to help with this, some of which are better than others; one comes with Windows but doesn't always get everything.

EDIT: Where's my head? If you've already freed up the partition, just select the "use largest contiguous free space" option when installing.

---

### Post by blazercist on 2008-12-03
You've already answered your own question.  If you already have a partiton set up to install ubuntu on then you don't need to defrag.  If you were planning on letting the installer resize your windows partition to create space for ubuntu then you need to defrag.

---

### Post by Halo_gg on 2008-12-03
Thanks guys. I will do it properly. Cheers!

---

### Post by Herman on 2008-12-03
It's a good idea to defrag your Windows partition before resizing it with the Ubuntu  'Alternate CD' installer's partitioner, 'partman'. 
When the 'Alternate CD' was the only one, most people used to install without defragging anyway, and most people got away without any problems.
Occasionally, there would be a post in the forums here about partman refusing to resize someone's Windows partition, but a little defragging normally rectified that problem.

The GParted Partition Editor was developed and the Ubuntu 'Desktop' Live/Install CDs came into being, and mostly replaced the 'Alternate CDs'
Gnome Partition Editor has always been able to resize Windows FAT32 or NTFS partition regardless or in spite of the state of fragmentation of the Windows file system. It does not make any difference to GParted at all.
However, it is advised in the documentation at GParted Live CD's web site, to run CHKDSK after resizing an NTFS partition. 
I would suggest running CHKDSK before-hand maybe, as well, just to be careful.
There's no need to bother defragging Windows if you're using GParted. :)

---

### Post by Halo_gg on 2008-12-03
> **Herman said:**
> It's a good idea to defrag your Windows partition before resizing it with the Ubuntu  'Alternate CD' installer's partitioner, 'partman'. 
When the 'Alternate CD' was the only one, most people used to install without defragging anyway, and most people got away without any problems.
Occasionally, there would be a post in the forums here about partman refusing to resize someone's Windows partition, but a little defragging normally rectified that problem.

The GParted Partition Editor was developed and the Ubuntu 'Desktop' Live/Install CDs came into being, and mostly replaced the 'Alternate CDs'
Gnome Partition Editor has always been able to resize Windows FAT32 or NTFS partition regardless or in spite of the state of fragmentation of the Windows file system. It does not make any difference to GParted at all.
However, it is advised in the documentation at GParted Live CD's web site, to run CHKDSK after resizing an NTFS partition. 
I would suggest running CHKDSK before-hand maybe, as well, just to be careful.
There's no need to bother defragging Windows if you're using GParted. :)

This is educational! Thanks mate!

---

