---
title: "Hard drive space: 0 bytes"
date: 2008-06-23
forum: Hardware
---

### Post by thexaspect on 2008-06-23
Ok, this is a really weird issue. Basically, I just finished loading(reloading) hardy. I had to reinstall over a previous installation because i loaded xp onto the drive, and it borked grub. easiest way i've found to fix that is to just reload ubuntu over the previous install, copying over the settings and whatnot and not repartitioning the drive. normal boot up after the fact, of course about 200 updates to download and install. fire up update manager, starts installing, all is well, and i'm showing in nautilus free space: 0 bytes. also, and it may be unrelated, but for whatever reason i'm no longer given the option to use my back button in firefox. wish i could throw some numbers and sweet cli results at you, but i really dont even know where to start. anybody got anything? 

by the way it's a 160GB hard drive, / is ~100GB, swap is about 4GB, ntfs(windoze) is ~40GB.

---

### Post by Odrodzona-Sarmacja on 2008-06-25
If you can, then do "save all markings" in synaptic manager into a text file

1. Resize swap partition to 1gb
2. Resize root partition from 100gb to 20gb
3. Create home partition (ext3) and give it all your free space

(And copy contents of your entire "/home" directory to your new partition. Dont create there /home directory on this partition just copy its contents. If you can that is)

4. Format your root partition from ext3 to fat32
5. Secure erase your new fat32
6. Create new clean root partition with these 20gb
7. Install your ubuntu with manual partitioning and offline from internet and point to root partition, swap partition and home partition, but do not mark home partition to format ever if you need to reinstall it over or something like that. ( When your ubuntu is installed and you logged in into it, then connect to internet and in synaptic manager load your markings.) Do update an update in synaptic manager.

Good luck. (Next time you need reinstall ubuntu you won't miss any personal settings and all your preferred apps will load from some markings text file, so the entire process will be quite fast)

---

### Post by johnapeterson on 2008-06-25
I am having the exact same problem.  Everything was just fine a couple of days ago, but now I am being told I have 0 bytes of free space.  I have a 160 gig hard drive, and it had about 90 gigs free a few days ago.

Help

---

### Post by Odrodzona-Sarmacja on 2008-06-26
> **johnapeterson said:**
> I am having the exact same problem.  Everything was just fine a couple of days ago, but now I am being told I have 0 bytes of free space.  I have a 160 gig hard drive, and it had about 90 gigs free a few days ago.

Help

Try mounting this hard drive on some new directory and access it through this new mount point.

"sudo mkdir /media/<new directory>"
"sudo mount /dev/<hard drive> /media/<new directory>"

now open you file browser and go to that mount point and look how much free space you have it on it.

---

