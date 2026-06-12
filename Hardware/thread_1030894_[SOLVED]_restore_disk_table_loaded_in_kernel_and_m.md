---
title: "[SOLVED] restore disk table loaded in kernel and mounted but missing from disk!"
date: 2009-01-04
forum: Hardware
---

### Post by ahelmick on 2009-01-04
I have been writing a piece of software for months... my total project folder is around 30gig.

My internal hard drive on my compaq Nx7010 floundered and crashed and it is an older laptop so I am not completely surprised.  I have a Seagate Freeagent Go attached and velcro'd to the lid and all my data was backed up. (USB external drive)

So I am booted to Ubuntu (latest version, booted by cd as my internal drive is dust) and I am attempting to partition the drive in such a way that I can install Windows (necessary evil) but mostly to re-install Ubuntu...

I use fdisk and the p command to view tables... I take the free space and make a new partition and the w to write...

error: (21 I think it was) changes will not be written until reboot, kernel retains current partitions...

SO... my current 2 partitions (not the new one I tried to create) are mounted and working and contain my 30 gig of work that I need to deliver next week.  I am afraid to reboot as fdisk gives error and will not load and the partition manager states that my entire disk is unallocated.

However, I can still access the mounted partitions...as they are still loaded in the kernel.

HOW DO I LOAD THEM BACK TO THE DISK TABLE!  Please... I cannot burn to CD, as the CD is the OS and is booted right now... (Live Disk boot Ubuntu) and I cannot seem to offload the data via Internet as it times out due to size.

I need to make sure that I do not lose 6 months worth of work that I am one week away from delivering.  How do I reload the disk table that is stored in the kernel to the disk.

Again... the partitions are currently mounted and accessible... fdisk floundered when I tried to allocate the free space and now NONE of my partitions show up via disk.  But, I can access them using mount.

I am afraid to reboot or turn the computer off.  I have been uploading 500 meg a day using my Internet (upload limit) to online storage but this will take another 6 days to complete.

I might be also to load drivers for the LAN (RJ-45) and copy to another computer, if I wasn't 100's of miles away from home and I know not a soul!

Your help is greatly appreciated.

Again, how do I take the disk table residing in kernel memory and write it back to the disk?

---

### Post by ahelmick on 2009-01-05
I figured it out myself!

I used sfdisk to dump a copy of the partition table stored in the kernel (loop) then I used the specs to upload the table into the disk (msdos partition table type) and THEN I used parted to do a recovery and THEN I copied the loop partition over the msdos partition to ensure the data was there...

It worked!  So if you blow a Ubuntu partition table it IS possible to recover it and any data EVEN if you have written to the partition and written a new partition table.

---

