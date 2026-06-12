---
title: "Using 10K 35GB SATA plus Two 750GB Sata in RAID"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by misterfixit on 2009-04-25
I want to set up my new install like this:

35GB SATA 10,000 rpm HD with new install;

2 x 750GB 7,500 rpm HD's in a RAID-10

I've read that there are some tricks to go through to use the RAID-10 set up.

Anyone have advice?

My goal is speed and recovery of vital data on the RAID array.

You think it would be easier, simpler to just put the essential company data on one 750GB and the p@rN on the other drive rather than mess with RAID???

Thanks in advance,

Dave

---

### Post by pparks1 on 2009-04-25
I assume that you meant that you wanted to use either RAID 0 (a stripe, with no protection whatsoever.   You get 100% of disk space, but if either drive fails, you lose them both), or you meant RAID 1 (Mirror, full redundnacy, but you only get 1/2 of total disk space...since second drive is mirror of the first).

The concept of RAID 10, which is a Mirror of a stripe, requires at least 4 hard drives of the same same.  You have to stripe 2 x 750 to get a 1.5TB drive, and then you mirror to the second 2 x 750 which are also in a RAID 0 stripe.   So, in the end, you get 50% of your total drive space, since you technically would have 4 x 750GB drives...but only get 2 x 750GB of usable space.

If this is for corporate data and a business, I would do some type of redundancy.  For my work servers, it's typically a RAID 1 mirror of the Operating system drives, and a RAID 5 array of the data disks.  All on hardware based server controllers for the best performance.

---

### Post by misterfixit on 2009-04-25
> **pparks1 said:**
> I assume that you meant that you wanted to use either RAID 0 (a stripe, with no protection whatsoever.   You get 100% of disk space, but if either drive fails, you lose them both), or you meant RAID 1 (Mirror, full redundnacy, but you only get 1/2 of total disk space...since second drive is mirror of the first).

The concept of RAID 10, which is a Mirror of a stripe, requires at least 4 hard drives of the same same.  You have to stripe 2 x 750 to get a 1.5TB drive, and then you mirror to the second 2 x 750 which are also in a RAID 0 stripe.   So, in the end, you get 50% of your total drive space, since you technically would have 4 x 750GB drives...but only get 2 x 750GB of usable space.

If this is for corporate data and a business, I would do some type of redundancy.  For my work servers, it's typically a RAID 1 mirror of the Operating system drives, and a RAID 5 array of the data disks.  All on hardware based server controllers for the best performance.


Ah, I understand .. well, pretty much anyway :-).

I think RAID-1 is what I want ... I bought the two 750GB drives from NewEgg just for the purpose of redundancy.  If I have your advice and my tired brain together, I can set up the two 750's as RAID-1 and even if one fails completely, I still have all of the data -- presumably through some kind of hocus-pocus recovery.  I mount the actual OS on the 10K RPM drive, thus achieving that little bit of extra speed that is probably all in my imagination but which makes me feel better.  The new box has 8GB of RAM and a pretty fast AMD64 cpu, so things are running well so far.  Mainly, I have about 5 or 6 of the available screens open at the same time, each with a different app on one (email, web, freecell, gimp, music, cobol punch card simulation, etc).  So it is nice to have a very fast box that I can do my ADD-like shifting between apps with the simply twist of a wrist and mousy wheel.

I am going to proceed with setting up 1x 35GB with the system on it, and then the 750 RAID with /home on it (them).

Sound like a plan ... this is my first RAID so I am nervous as a teenager the first time in the backseat of his dad's 56 Chevy.

Dave

---

### Post by misterfixit on 2009-04-28
> **misterfixit said:**
> Ah, I understand .. well, pretty much anyway :-).

I think RAID-1 is what I want ... I bought the two 750GB drives from NewEgg just for the purpose of redundancy.  If I have your advice and my tired brain together, I can set up the two 750's as RAID-1 and even if one fails completely, I still have all of the data -- presumably through some kind of hocus-pocus recovery.  I mount the actual OS on the 10K RPM drive, thus achieving that little bit of extra speed that is probably all in my imagination but which makes me feel better.  The new box has 8GB of RAM and a pretty fast AMD64 cpu, so things are running well so far.  Mainly, I have about 5 or 6 of the available screens open at the same time, each with a different app on one (email, web, freecell, gimp, music, cobol punch card simulation, etc).  So it is nice to have a very fast box that I can do my ADD-like shifting between apps with the simply twist of a wrist and mousy wheel.

I am going to proceed with setting up 1x 35GB with the system on it, and then the 750 RAID with /home on it (them).

Sound like a plan ... this is my first RAID so I am nervous as a teenager the first time in the backseat of his dad's 56 Chevy.

Dave


OK, I got the Box put back together again ... did some work on cooling and making the cables neat ...etc.

What I have now is 2 x 750GB SATA drives and a 1 x 36GB SATA drive.

I used the BiOS RAID setup routine which is announced during the BiOS boot sequence, to establish the two 750GB drives at a RAID 1 array.  I loaded Ubuntu 9.01 onto the 36GB drive.  

Everything rebooted fine, all undates installed, and essentially, the system is back to normal -- Voila!  -- Not that I didn't think it woldn'tbe.

OK, now as to the 750GB storage system.  

Parted shows that I have /dev/mapper/nvidia_bbdjeeg (698.64)  ... this must be the two 750GB drives mapped together as RAID 1 by the on-MoBo BiOS RAID system.

Parted also showed the two individual drives (dev/sdb and /dev/sdc).

They show as unknown format -- which tells me that they have not yet been formatted. (which I have not yet done)

Questions:

Shall I use parted to format the individual /dev/sbd and /.sbc to ext3 and then reboot the system to make the BiOS RAID controller see the devices as formatted?

So far so good with all of your help.

Thanks in Advance for the help!

Dave

---

### Post by ronparent on 2009-04-28
**NO!!!** Do not format the individual drives. The raid array shows up as a separate drive in itself in gparted. Create all of your partitions on the array. Dmraid will take care of mapping it out for you automatically. Especially important if you already have data on the array you wish to recover. Incidently one of the new partitions can be /home.

---

### Post by misterfixit on 2009-04-28
> **ronparent said:**
> **NO!!!** Do not format the individual drives. The raid array shows up as a separate drive in itself in gparted. Create all of your partitions on the array. Dmraid will take care of mapping it out for you automatically. Especially important if you already have data on the array you wish to recover. Incidently one of the new partitions can be /home.

Thank You!  I haven't touched anything yet ... :-)

I'm setting the raid array as ext4 as I type this back to you.  Thanks for the help!  Here is what the Gparted output looks like, which I post here so that others may learn from this :-)

======================

GParted 0.4.3

Libparted 1.8.8
Create Primary Partition #1 (ext4, 698.64 GiB) on /dev/mapper/nvidia_bbdjeehg  00:04:22    ( SUCCESS )
     	
create empty partition  00:00:11    ( SUCCESS )
     	
path: /dev/mapper/nvidia_bbdjeehg1
start: 63
end: 1465144064
size: 1465144002 (698.64 GiB)
set partition type on /dev/mapper/nvidia_bbdjeehg1  00:00:11    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:04:00    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "The-Mighty-Wurlitzer" /dev/mapper/nvidia_bbdjeehg1
     	
Filesystem label=The-Mighty-Wurli
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
45793280 inodes, 183143000 blocks
9157150 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
5590 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
102400000

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.4 (27-Jan-2009)

---

### Post by misterfixit on 2009-04-28
Now that I have the RAID array ready.  I want to create /mnt/RAID and then /mnt /dev/{raid array info} /mnt/RAID

How does that sound; or should I be able to see the RAID array as a /dev displayed as an icon when I click on "Places" and "My COMputer" ??

---

### Post by ronparent on 2009-04-28
You could see it on your desktop if you wanted by mounting it in /etc/fstab. I currently have selected windows partition so mounted. Simply link your symbolic link for the partition found in /dev/mapper to your mount point. If the directory you want it to appear in doesn't exist you create it wherever you want it(ie /media/The-Mighty-Wurli/). Congratlulations. I think you have it about made!

---

### Post by misterfixit on 2009-04-30
OK, sucess on all.  I did what you said and then a cold reboot.  The RAID array is actually shown as an icon in the "places" area of the top drop down menu.

I've placed all of my folders, some 200 GB of video, photos, music, documents and ebooks on the RAID system.  I am going to relocate /home there this week end.  As I moved the files from the other drives ( a couple of SATA and an old 200GB IDE) I simply disconnected the drives and eventually reduced the system to the 3 SATA drives.

This is now a very fast system:

AMD64 3Ghz
8GB of RAM
10K Rpm 36GB SATA with the system
2x 750GB 7.5K SATA with the other stuff

Sweet.

I believe that because I was patient, RTFM, waited to figure things out, got help when I needed it (not after I screwed things up), that this turned out to be an effortless job.

Thanks for the help!

---

