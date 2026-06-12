---
title: "Copy boot disk to ram, then run from it - possible?"
date: 2008-08-27
forum: General Help
---

### Post by Krupski on 2008-08-27
Hi!

I'm running a stand-alone file server using Ubuntu v8.04.1 64 bit server with hard drives as RAID and a solid state Compact Flash card as the boot device (i.e. Linux boots and runs from Compact Flash, the hard disks are purely for data storage).

To avoid ruining the lifespan of the flash memory in the CF card, I am wondering if it's possible at boot time to COPY the CF card's data to ram (a ramdisk?) and then run from the ram image?

My goal is to avoid writing to the flash memory all the time.

I picture reading the boot image from the CF card to ram and running off that.

ONLY upon shutdown would the running ram image be "sync'd" back to the CF card (i.e. only one write cycle per reboot).

Is this possible? If so, please do tell how!

Thanks.

-- Roger

---

### Post by PeterBBB on 2008-08-27
Hi,

The Ubuntu ramdisk is /dev/shm

Pete

---

### Post by oilchangeguy on 2008-08-27
> **Krupski said:**
> Hi!

I'm running a stand-alone file server using Ubuntu v8.04.1 64 bit server with hard drives as RAID and a solid state Compact Flash card as the boot device (i.e. Linux boots and runs from Compact Flash, the hard disks are purely for data storage).

To avoid ruining the lifespan of the flash memory in the CF card, I am wondering if it's possible at boot time to COPY the CF card's data to ram (a ramdisk?) and then run from the ram image?

My goal is to avoid writing to the flash memory all the time.

I picture reading the boot image from the CF card to ram and running off that.

ONLY upon shutdown would the running ram image be "sync'd" back to the CF card (i.e. only one write cycle per reboot).

Is this possible? If so, please do tell how!

Thanks.

-- Roger

why make life hard? just install the operating system on the computer. it doesn't take up that much space.

---

### Post by Krupski on 2008-08-27
> **PeterBBB said:**
> Hi,

The Ubuntu ramdisk is /dev/shm

Pete

Thank you! Yes I know about /dev/shm.

What I want to do is, at boot time, copy the entire Ubuntu disk image (about 700 mb) to system ram, then unmount the compact flash card and mount the ram image.

The idea is to minimize read/write cycles to the limited lifespan compact flash card (Flash memory wears out after 100K to 1M write cycles).

I foolishly tried to simply copy '/' to the /dev/shm drive. Of course, it failed because /dev/shm is a directory of the root '/' so it just kept going and going recursively until it ran out of space (of which I have 8GB ram). :)

Thanks anyway!

-- Roger

---

### Post by Krupski on 2008-08-27
> **oilchangeguy said:**
> why make life hard? just install the operating system on the computer. it doesn't take up that much space.

The OS *is* on the computer. The setup is like this:

* 1 drive, solid state compact flash 4GB (boot, OS). 2GB for the OS, 2GB for swap.

* 4 drives, mechanical hard drives, 1TB each setup as RAID 0+1, yielding 2 TB of SAMBA storage, striped and mirrored.

It all works nicely. What I would LIKE to do is this:

* Boot from Compact Flash
* Copy Compact Flash drive (the OS) --> RAM
* Mount RAM, unmount Compact Flash
* Run OS in ram


I can copy directories from the root into /dev/shm, but since it's a "drive" and not a block device, I can't mount '/' to it!

Alternately, I could specify a usable ramdisk size in menu.lst (GRUB), but I only need ONE large ramdisk, not 16!

And, I don't know how to either change HOW MANY /dev/ram* devices Ubuntu makes OR how to set the size of just ONE of them.

:(

Oh well... gotta keep searching Google!

Thanks!

-- Roger

---

### Post by sdennie on 2008-08-27
You could probably do something like this using tmpfs.  I mount various parts of the system as tmpfs and then use /etc/rc.local to populate them and cronjobs to write the changed data back to disk every 10 minutes (I do this so I can keep the disks spun down for power savings).  

However, this is probably overkill in the case you are talking about and may not actually lengthen the lifespan of the disk because very, very few parts of the system are written during normal operation so, really, you are just going through a huge hassle to delay those writes until shutdown.

My advice would be to look at this guide: [http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive) and possibly this one: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998).  Using both will probably cause your CF card to last longer than the average hard drive.

(One last note: If you think you will ever actually use swap, I wouldn't mount it on the CF.  That will decrease the lifetime significantly.)

---

### Post by Krupski on 2008-08-27
> **vor said:**
> You could probably do something like this using tmpfs.  I mount various parts of the system as tmpfs and then use /etc/rc.local to populate them and cronjobs to write the changed data back to disk every 10 minutes (I do this so I can keep the disks spun down for power savings).  

However, this is probably overkill in the case you are talking about and may not actually lengthen the lifespan of the disk because very, very few parts of the system are written during normal operation so, really, you are just going through a huge hassle to delay those writes until shutdown.

My advice would be to look at this guide: [http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive) and possibly this one: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998).  Using both will probably cause your CF card to last longer than the average hard drive.

(One last note: If you think you will ever actually use swap, I wouldn't mount it on the CF.  That will decrease the lifetime significantly.)

Thank you! I'll check those links.

You're right about swap. My swap partition is currently on the CF card (yeah it was a dumb thing to do). I plan to move it to the hard drive.

Thanks again!

--- Roger

---

### Post by Jerry.S on 2008-08-27
I know its not ubuntu but go over to freeNAS and take a look at how they do it with just a CF card and adapter. it is not a file server but it will work :)

---

### Post by utUtu on 2008-08-27
You should look at how the live distros do it.  Usually, they run in ram especially those small ones like - Puppy, slax.  There is the toram boot option.  I remember even the Fedora live beta was running so fast bec it copied itself to my 4gig ram.

---

