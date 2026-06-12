---
title: "/etc/fstab Question."
date: 2008-11-07
forum: General Help
---

### Post by Roasted on 2008-11-07
If I have four SATA drives in my computer during the initial install of Ubuntu, does /etc/fstab detect them and put them into /etc/fstab to automatically mount when I start Ubuntu?

Reason I ask is, I can't remember how I installed Ubuntu. I don't know if I installed it with 1 SATA drive in or 4 SATA drives in.. because I had to find the UUID of each hard drive and put it into /etc/fstab so the disks would automatically mount to their designated folder in the media directory.

Also, if I installed Ubuntu with 4 SATA drives plugged in, but 3 of the drives are simply backup drives that weren't touched, if I unplug those SATA drives and take them out, would it prompt me with a grub error when I start up since a drive is missing, even if it's not the actual boot drive? 

So I guess realistically this isn't 1 question, it's more like 5 or 6. :guitar::lolflag:

---

### Post by _sAm_ on 2008-11-07
> If I have four SATA drives in my computer during the initial install of Ubuntu, does /etc/fstab detect them and put them into /etc/fstab to automatically mount when I start Ubuntu?
No. It will only end up in /etc/fstab if you during installation tells the system to mount them(you can add them and tell to do nothing). Or if you later add them to the list.
Just run nano /etc/fstab to see what is listed and compare it with fdisk -l

> Also, if I installed Ubuntu with 4 SATA drives plugged in, but 3 of the drives are simply backup drives that weren't touched, if I unplug those SATA drives and take them out, would it prompt me with a grub error when I start up since a drive is missing, even if it's not the actual boot drive?
Dont think so.

---

### Post by Roasted on 2008-11-07
But I can't create directories within the installation utility, can I? Because in the media directory I have 3 folders that I mount the other 3 drives to respectively. LocalBackup, Storage, StorageBackup...

I can't create folders like that in /media during the installation process, can I? If I can, I can see how I would be able to mount the 3 SATA drives to their respective folders.

I just only recall being able to mount to root, home, etc during the install.

---

### Post by dabl on 2008-11-07
> **Roasted said:**
> But I can't create directories within the installation utility, can I? Because in the media directory I have 3 folders that I mount the other 3 drives to respectively. LocalBackup, Storage, StorageBackup...



During the 8.10 installation process, at the "Partitioning" phase, if you choose "Guided" you have the ability to put a checkmark in front of each partition/drive that you want automatically mounted.  So that's how you "create directories" during installation.

> 

I can't create folders like that in /media during the installation process, can I? If I can, I can see how I would be able to mount the 3 SATA drives to their respective folders.



You can certainly create directories in /media, anytime you wish.  ```
sudo mkdir /media/newfolder
``` will do the trick every time.

> 

I just only recall being able to mount to root, home, etc during the install.

That was more true in earlier versions.  But it's always been the case that you could open the console, make suitable directories in /media, and then edit /etc/fstab to set them to automatically be mounted during the boot process.  :)

---

### Post by drs305 on 2008-11-07
> **Roasted said:**
> I just only recall being able to mount to root, home, etc during the install.

As dabl stated, you can do it during setup if you select guided or manual. You specify the partition and then in the mount window, instead of selecting one of the predesignated mount points (/, /home, /swap, etc) you can just type in the desired mount point (e.g. /media/mymusic). Don't forget to select or not select 'format' or you may wipe out a data partition that already exists.

---

### Post by Roasted on 2008-11-07
dabl - I don't mean to sound like I didn't listen to you, but I have a question building on what you just told me... sorta.

I just booted to my LiveCD. I have a LiveCD with my stack of CDs with me at work, I use Ubuntu for troubleshooting reasons (gparted, etc). I booted up to it and went to step 4 (partitioning) of the installer. I went to manual. Where the mount point was, there's a dropdown list. I partitioned my hard drive (I only have 1 in this laptop, but two partitions should react the same way two hard drives would) and I made a 10gb plus a 70gb partition.

I mounted the 10gb partition to root.
For the 70gb partition, instead of hitting the drop down box for root, home, etc... I just typed in it... "/media/storage"

If I do that, would it create /media/storage and automatically mount to that? Or do I have to do what you said, and with the LiveCD running go to /media and sudo mkdir storage? 

I'm just having a hard time seeing how creating the folder on a LiveCD would be seen by the LiveCD installer... know what I mean? 

But hey guys, thanks for your help. Much appreciated. If I can get some built up responses on what I just asked I'll be a happy camper. :guitar:

---

### Post by drs305 on 2008-11-07
> **Roasted said:**
> I mounted the 10gb partition to root.
For the 70gb partition, instead of hitting the drop down box for root, home, etc... I just typed in it... "/media/storage"

If I do that, would it create /media/storage and automatically mount to that? Or do I have to do what you said, and with the LiveCD running go to /media and sudo mkdir storage? 

What you have done should be sufficient. You shouldn't have to make the mount point again.

> 
I'm just having a hard time seeing how creating the folder on a LiveCD would be seen by the LiveCD installer... know what I mean? 

You are actually at the partitioning stage. When you opened up the partitioner during installation, it looked at your physical system and saw your devices and how they are paritioned. You aren't creating a folder on the LiveCD, you are making it on an actual device.

---

### Post by Roasted on 2008-11-07
Soooo realistically by commanding the LiveCD in the partitioner to "mount /dev/sda1 to /media/storage" it'll actually create the storage directory accordingly.

Next question is, assuming what I said above is true, say I go through the install and everything gets done and installed.

If I go into /etc/fstab, /dev/sda1 that is mounted to /media/storage, will it be connected to /media/storage by UUID? Or by the device tag? (/dev/sda1)

---

### Post by drs305 on 2008-11-07
> **Roasted said:**
> Soooo realistically by commanding the LiveCD in the partitioner to "mount /dev/sda1 to /media/storage" it'll actually create the storage directory accordingly.

Next question is, assuming what I said above is true, say I go through the install and everything gets done and installed.

If I go into /etc/fstab, /dev/sda1 that is mounted to /media/storage, will it be connected to /media/storage by UUID? Or by the device tag? (/dev/sda1)

I believe everything is still done with the device designation although I haven't run the install in Intrepid yet. You can change it after installation by finding the uuid with "sudo blkid".

By the way, in case you didn't see what I posted about the same time as one of your other posts. Don't forget to check to ensure you don't format a partition that has data on it (make sure the 'format' box is unticked).

---

### Post by Roasted on 2008-11-07
> **drs305 said:**
> I believe everything is still done with the device designation although I haven't run the install in Intrepid yet. You can change it after installation by finding the uuid with "sudo blkid".

By the way, in case you didn't see what I posted about the same time as one of your other posts. Don't forget to check to ensure you don't format a partition that has data on it (make sure the 'format' box is unticked).

Oh yeah, I know.

When I "simulated" the manual partitioning process on this laptop, it forced me to have the checkbox checked because I was creating an entirely new partition. I would assume if the partition on the backup SATA drives already existed that it wouldn't require me to format them. Which... would be nice.

I would just be kind of shocked to know that they install based on device tag instead of UUID, especially when going in to the actual installer.

I think when I get home what I should do is pull my SATA drives and plug in a spare 200gb IDE I have and partition it accordingly, and see how it reacts to me making a 10gb root partition and a 190gb partition on /media/storage and see exactly what it does... whether it uses UUID or not.

---

### Post by dabl on 2008-11-07
I don't know for sure when it will set up the mount point as you typed it in, or just arbitrarily make it /media/disk1 and /media/disk2, etc.  But, if you mark a partition to be mounted, then it will be mounted as something or other.

Obviously you can later edit the mount point in /etc/fstab and /media/disk2 and change them both to /media/VIDEOS or whatever you wish.

@roasted, if you're going to do experiments with making partitions on a drive, I highly recommend you make a GParted Live CD, and use that. I've always found it preferable to do the partitioning first, and not get that process intermingled with the installation process.  Here's where you get the ISO for a GParted Live CD:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

;-)

---

### Post by drs305 on 2008-11-07
I agree with dabl - I usually do my partitioning with gparted before starting an installation. One thing I do differently though is that I made and use a SystemRescueCD, which has gparted and other utilities on it. Here is the link if you are interested:
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by Roasted on 2008-11-07
Thanks guys. I actually have a GParted LiveCD somewhere... I've just never really done things in that order. I've always went right to the install and tinkered with things the way I wanted during the install. I'll give it a shot, though.

Has anybody ever used multiple drivers installing and just left the installer randomly assign the extra HDD to /media/disk or whatever? If so, to anybody who's reading this who that may apply to, check your /etc/fstab... I'm VERY curious to know if it's assigned by UUID or not...

---

### Post by Roasted on 2008-11-10
Update to what I was curious about.

In a spare system, I put an 80gb IDE hard drive in the system and booted up and installed Ubuntu Intrepid 32 bit.

I made 5 partitions.

10gb - root
12gb - backup
15gb - backuptwo
20gb - anotherbackup
23gb - finalbackup

I mounted all of these within the partition editor prior to the Ubuntu installer taking over. So where you hit the drop down menu to select "/" for root, I simply typed /media/backup, or /media/backuptwo, etc. 

It seems to work fine. I booted up and checked my /etc/fstab, and each partition is mounted by the UUID, which I had to manually do before. So at least I know I can set everything up in the partition editor before I do an actual installation in the future. Or, in my case, I can at least mount my backup drives WITHOUT formatting them and without having to run "blkid" and input the UUID's into /etc/fstab, even though that's an easy step.

The real question I have is how /etc/fstab is set up now in this spare computer. To give you one example, we'll look at the 12gb partition I made.

It has the UUID followed by /media/backup ext3 relatime 0 2

Remember how I used defaults 0 0? This did relatime 0 2 on its own.

What does that mean? How does it differ from defaults 0 0?

---

### Post by drs305 on 2008-11-11
Relatime is a default setting which detemines how and how often a file's information is checked. You generally don't have to deal with it unless you are truly into geekdom. Here is a link explaining it:
[http://lwn.net/Articles/244829/]("http://lwn.net/Articles/244829/")

The last digit in the line detemines fsck checking. Root is normally set at 1. Other ext2/3 devices are set to 2 (lower priority than root but still checked periodically). Non-linux partitions are set to 0, since fsck doesn't perform checks on them anyway.

---

### Post by Roasted on 2008-11-12
So it's "probably" in my best interest to use 0 2 instead of 0 0?

---

### Post by drs305 on 2008-11-13
> **Roasted said:**
> So it's "probably" in my best interest to use 0 2 instead of 0 0?

Yes.

---

### Post by Roasted on 2008-11-23
> **drs305 said:**
> Yes.

Is it possible I can check these disks while the system is running as opposed to doing it every 30 reboots?

---

### Post by drs305 on 2008-11-23
> **Roasted said:**
> Is it possible I can check these disks while the ***system*** is running as opposed to doing it every 30 reboots?

Yes, with a warning not to run the check on any *mounted* device. The command would be "sudo fsck /dev/unmounted.device.designation", e.g. sudo fsck /dev/sdb10.

You can also manually schedule an fsck check on the next bootup by running this command in the root of the device you want to check. The advantage is you can use this for any device, as they won't be mounted when it is run:
```
sudo touch /forcefsck
```

You can change how often fsck checks are performed with an app called 'tune2fs'. You can set the interval by mounts, days, etc. Read about it in the "man tune2fs" page.

---

