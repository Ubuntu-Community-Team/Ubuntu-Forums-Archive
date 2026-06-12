---
title: "Cannot install on new HDD, just want one OS."
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by RRK on 2009-08-08
I had a windowsXP system annihilated by trojans and rootkits viruses.... I am done with windows.  I have run Ubuntu for a couple of years now on another PC and I like it so I am updating the family PC to Ubuntu.
Pentium 4 Prescott 3.2gHz with 64T support, 2GiB ram (2x1GiB). The old drive is cleaned of windows and programs, only thing left are music, docs, movies, etc in a NTFS partition on that drive.

I bought a new hard drive (exact same one I use on my running-Linux PC). WD caviar blue 160 GiB. It's connected to SATA port 0, and the old drive is connected to port 1.

I have tried installing Ubuntu 8.10 64-bit, Ubuntu 9.04 64-bit, and Puppy (which installed just fine on my daughters 1999 Compact laptop).

All three live cd's run fine.

The installs are failing. Either with ERRNO 05 or ERRNO 30.

I added mount commands to /etc/fstab for the partitions I am trying to create. Not sure this was necessary.

/dev/hda1 /     ext3 defaults 0 1
/dev/hda2 /home ext3 defaults 0 2
/dev/hda3 swap swap defaults 0 0

I started the install again and the partitioning progress bar has only got to 24% for the 1st partition (15GiB) after about 30 minutes and then issued this:
___________________________________________

[COLOR="Blue"]The installer encountered an error copying files to the hard disk: 

[Errno 30] Read-only file system 

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.[/COLOR]
______________________________________________

The CD is burned at 4x.

This all seems to me that one of two things could be wrong.

1. the HDD is bad -- how would I check to see if it's good?  All the WD software is targeted to Windows or MS-Dos.

2. I don't know what I am doing. I didn't know what I was doing before and I have been running Ubuntu since Edgy Eft. So I am doubting this, but I may have missed something.  

Any ideas?

---

### Post by Partyboi2 on 2009-08-08
Hi, if you are wanting to check the hard drive you should be able to download 'Data Lifeguard Diagnostic for Dos (cd)' from the Western Digital website, then extract it, and burn the iso to a cd and boot from it.

---

### Post by Greg Xix on 2009-08-08
I personally have a Live USB installed on an old 1GB USB Flash disk. I used to sometimes get weird errors when installing from CD-RW's myself.

Not sure if you know how to make a Live USB:

1. download the 9.04 ISO file to Desktop

2. Use the GParted/Partition Editor tool to "format" the Flash disk. **DO NOT** Format it with a filesystem i.e. Fat32 or Fat16. Just leave it "Unallocated". I ran into problems when I did it that way. Let the ISO format/burn it how it wants to.

3. Goto System > Administration > USB Startup Disk Creator and mount/burn the ISO to the USB Flash disk

4. Of course then set your BIOS Boot Sequence to load from the USB Drive first, and hopefully it will install from there



This way has always worked like a charm for me. And it takes only about 15 mins to go from "Zero to fresh Ubuntu Install" on the Hard Drive, which is a lot faster than even when the CD installs actually did work. 

If this doesnt work I'd request an officially burned CD from Ubuntu directly, somebody today told me they are Free coincidentally, but take about 3 weeks to arrive in the mail. But you get a cool looking CD and some stickers.



-GX

---

### Post by dE_logics on 2009-08-08
> I added mount commands to /etc/fstab for the partitions I am trying to create. Not sure this was necessary.

No you can't do that.

All your systems and hard drives appear extremely old...so probability of a failing hard drive is pretty high.

Also, as said above, ensure you format the partition (into which you're installing) in native Linux file systems like ext3, 4 or it's actually recommenced to set it to reserfs (if 9.04 supports reserfs4...still better)...it's a pretty advanced FS...and very reliable.

Boot from the live CD and pose the result of ```
smartctl <device> -a
```

Place your hard drive name (sda or sdb etc...) in that device section...do this for both the hard drives.

It also might be that your other NTFS/FAT partitions have virtual bad sectors...in that case you have to format the whole hard drive. This is most probably the case if your hard drive says that it's healthy.

---

### Post by RRK on 2009-08-09
Tried the WD Data LifeGuard Diagnostic.  It hangs on "Starting Caldera DR-DOS". Searching the net I see this happens sometimes, I did not see a resolution.

I put the ISO on USB.  Install fails with:
[COLOR="RoyalBlue"]The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.[/COLOR]

Of my two drives.

320 Gib is 15 months old and contains the data I want to save.  I can get to it when I run the Live CD.

160 GiB I purchased 1 week ago. The only thing ever installed on it is a partial-unbootable Ubuntu

---

### Post by MacGoose on 2009-08-09
I have about the same problem installing the 9.04 netbook remix on my Eee 900.  I have done about everything I can think of when it comes to creating partitions and formatting them to different formats ( ext3 is the only one without error messages, but still, when finished formatting it says unknown file system ).

So I have tried creating partition tables and removing all partitions ( as it doesn't matter since the installation will remove old and create new ones anyway ).

Also I have noticed when checking the installation ( Check disc for defects ) it says there is an error in one file.  My MD5 check is correct though.

I'm thinking it can't be my HD as I had no problem with it earlier.  Anyway, I'm downloading Ubuntu again and hoping there was a problem with the download.

---

### Post by Partyboi2 on 2009-08-09
> **MacGoose said:**
> I have about the same problem installing the 9.04 netbook remix on my Eee 900.  I have done about everything I can think of when it comes to creating partitions and formatting them to different formats ( ext3 is the only one without error messages, but still, when finished formatting it says unknown file system ).

So I have tried creating partition tables and removing all partitions ( as it doesn't matter since the installation will remove old and create new ones anyway ).

Also I have noticed when checking the installation ( Check disc for defects ) it says there is an error in one file.  My MD5 check is correct though.

I'm thinking it can't be my HD as I had no problem with it earlier.  Anyway, I'm downloading Ubuntu again and hoping there was a problem with the download.
Try burning the iso to disk at a lower speed (x4 or less) there is probably some data corruption happening during the burning.

---

### Post by vegmunky on 2009-08-10
> **RRKillian said:**
> 1. the HDD is bad -- how would I check to see if it's good?  All the WD software is targeted to Windows or MS-Dos.

SpinRite. Run it at level 5. Let it run overnight if necessary. It's completely OS independent.

---

### Post by MacGoose on 2009-08-10
> **Partyboi2 said:**
> Try burning the iso to disk at a lower speed (x4 or less) there is probably some data corruption happening during the burning.

Sorry, cannot do.  The Eee has no CD drive so I'm doing it through an USB.  Gonna do a test on my HD too just to have done it.

---

### Post by RRK on 2009-08-10
I burned the ISO's, ubuntu and puppy at 4x. Does it matter that I burned them to a CD-RW? Does it need to be a CD-R? I am using Memorex brand. 

Could memory really be a problem as I have seen posted elsewhere? I have 2 sticks of DDR2, I don't think I can pull just one. Plus it doesn't make sense to me that the 9.04 install gets stopped by too much memory.

Spinrite is $90.  I can buy 2 more of the WD 160GB caviar drives for this price including shipping. I think I'll skip that. 

I am running e2fschk right now, hopefully that will be done when I get home tonight.

I have tried ext4, ext3, and ext2. 

Is there something that might be obvious to others that I may have missed? 
Sata drive on Intel platform and cpu. I have RAID turned off in the BIOS (I am not using the drive as a RAID drive). Could it need some special driver?

---

### Post by andrew84125 on 2009-08-10
I cannot install Ubuntu on my pc also. Anyone can help me by step by step instruction.
 
Thanks
 
 
 
> **RRKillian said:**
> I had a windowsXP system annihilated by trojans and rootkits viruses.... I am done with windows. I have run Ubuntu for a couple of years now on another PC and I like it so I am updating the family PC to Ubuntu.
Pentium 4 Prescott 3.2gHz with 64T support, 2GiB ram (2x1GiB). The old drive is cleaned of windows and programs, only thing left are music, docs, movies, etc in a NTFS partition on that drive.
 
I bought a new hard drive (exact same one I use on my running-Linux PC). WD caviar blue 160 GiB. It's connected to SATA port 0, and the old drive is connected to port 1.
 
I have tried installing Ubuntu 8.10 64-bit, Ubuntu 9.04 64-bit, and Puppy (which installed just fine on my daughters 1999 Compact laptop).
 
All three live cd's run fine.
 
The installs are failing. Either with ERRNO 05 or ERRNO 30.
 
I added mount commands to /etc/fstab for the partitions I am trying to create. Not sure this was necessary.
 
/dev/hda1 / ext3 defaults 0 1
/dev/hda2 /home ext3 defaults 0 2
/dev/hda3 swap swap defaults 0 0
 
I started the install again and the partitioning progress bar has only got to 24% for the 1st partition (15GiB) after about 30 minutes and then issued this:
___________________________________________
 
[COLOR=blue]The installer encountered an error copying files to the hard disk: [/COLOR]
 
[COLOR=blue][Errno 30] Read-only file system [/COLOR]
 
[COLOR=blue]This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.[/COLOR]
______________________________________________
 
The CD is burned at 4x.
 
This all seems to me that one of two things could be wrong.
 
1. the HDD is bad -- how would I check to see if it's good? All the WD software is targeted to Windows or MS-Dos.
 
2. I don't know what I am doing. I didn't know what I was doing before and I have been running Ubuntu since Edgy Eft. So I am doubting this, but I may have missed something. 
 
Any ideas?

---

### Post by zxlstoner on 2009-10-13
Hi, did you get the solution to "**Cannot install on new HDD, just want one OS.**"
It seems that I have the same problem with you. Every installation, when copying files to hard drive around 23%-33%, it pops with errno 30 saying that my hard drive or CD ROM is not correct. 
I have tried a lot of times, but I still cannot handle it. So I write to you and hope to get the answer.
thanks!

---

### Post by presence1960 on 2009-10-13
I kept getting that errno 5 error on a Live USB. I finally had to go back to square one and [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso I used to create the Live USB. The iso was no good. Downloaded another iso from a torrent and voila! when I made the Live USB the install went perfectly! Try downloading from a torrent instead of a direct download mirror.

---

