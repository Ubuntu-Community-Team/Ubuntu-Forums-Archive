---
title: "Best compatible filesystem"
date: 2009-09-11
forum: Hardware
---

### Post by fela on 2009-09-11
We're planning on getting a large (1-1.5TB) HDD purely to backup tonnes of data onto.

I'm wondering on what filesystem to use as it has to have reliable read/write support on Linux, OSX and Windows.

Of course there's FAT32 but surely I shouldn't use that to reliably back up 100s of GB of data, with some files being larger than 4GB (does FAT32 even support that?).

Bear in mind that I want to be able to connect it locally to each computer by ESATA, Firewire or USB, in contrast to just connecting it to the linux server and accessing it by something like NFS or Samba.

I've heard about ZFS and that it's great for large disks. Also do you know if Windows and OSX support XFS? I don't want to have to install a 3rd party driver on any of them as I wouldn't trust critical data to a 3rd party fs driver.

Thanks in advance

PS. any advice for what hdd manufacturer to use?

---

### Post by GoldenSun on 2009-09-11
Well Mac's can write to ntfs, they can only read.  Windows likes guys when it sees an extx filesystem.  
The only option I see here is try to cope with old fat32 for compatibility with all 3.  

I would suggest to just use it as a network drive so you don't have to worry about filesystem compatibility.  

Or get 2x 640gb drives have different filesystems on each.

---

### Post by fela on 2009-09-11
> **GoldenSun said:**
> Well Mac's can write to ntfs, they can only read.  Windows likes guys when it sees an extx filesystem.  
The only option I see here is try to cope with old fat32 for compatibility with all 3.  

I would suggest to just use it as a network drive so you don't have to worry about filesystem compatibility.  

Or get 2x 640gb drives have different filesystems on each.

You mean macs *can't* write to NTFS :)

If I have it as a network drive I'd have to make a firewire network as 10/100 ethernet is way too slow to be backing up gigabytes at a time, in my opinion.

I guess I'll have to experiment with FAT32 :S

---

### Post by jmate24 on 2011-10-28
fat32 cannot save files larger than 4GB.

---

### Post by coffeecat on 2011-10-28
Go back to sleep thread.

---

