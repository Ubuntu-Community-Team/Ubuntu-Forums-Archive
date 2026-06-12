---
title: "Computer Partition Errors"
date: 2012-04-22
forum: Hardware
---

### Post by evanzo23 on 2012-04-22
Okay, so I figured that I would come here to ask for a little help with my computer. Here goes...

Yesterday I was repartitioning my hard drive to add on a third part that  was about 40 gigabytes for ubuntu (which would have come from my initial partition  that I was shrinking with gparted, but in the midst  of shrinking the largest partition to make room, gparted crashed. I  don't know why, but it did. With it having crashed, I have no means to  access my Windows Partition. Gparted labels my windows partition as  unknown, and I can only format it from that application. If I tried to  boot into Windows, it would display 'No operating system...." In order  to try to regain access, I fix just check to see if the boot record was  faulty by using the windows installation disk and bootrec (It had  happened before that the bootloader went funny, but never like this).  Much to my dismay, it left me with no change. Saddened by that and the  everlasting formatting type that not even God would label for gparted, I  tried to see if testdisk could save me. It didn't, and I am left at  booting windows to a blinking cursor. I don't know where to go, so any  help would be appreciated.

(And I am truly sorry if you find this to be in the wrong location on the forums, but I thought this section was fairly appropriate)

---

### Post by ahallubuntu on 2012-04-22
Google for "partition recovery" software.  You may be able to recover many/most of the files in your original partition with file recovery software (google for that too), but I'm guessing once you get those files back you are looking at a fresh install of Windows.  I've used Recuva for recovering files from NTFS partitions, but those partitions were not damaged like yours is (Gparted was moving files around so it could be a mess).   Some file recovery software can recover files from damaged partitions I'm pretty sure but I've not used that software.

It could be you will be lucky enough to restore your original partition table and then run chkdsk and most of your files will be fine.  Cross your fingers.

I don't know why people don't get the message that they need to make regular backups of their data.  Even if you aren't doing something as risky as a partition shrink, hard drives fail every day, sometimes without warning, and you lose EVERYTHING on the drive.  I had it happen to me once years ago - never again.  I've seen it happen to numerous people, too, people who claim they knew they should backup but never got around to it.  Oh, well.

In the future, besides making a backup of your important data on a separate device(!), here are a few tips for shrinking a Windows partition:

- turn off hibernation temporarily and delete the hiberfil.sys file.
- turn off PAGING temporarily and delete your pagefile.sys file (after rebooting).
- defrag your hard drive if it needs to be.  Twice wouldn't be a bad idea.
- THEN try shrinking your partition.  It will be way easier if you have done the above.
- in Windows, turn PAGING back on; turn hibernation back on if you had it on before.

---

### Post by Mark Phelps on 2012-04-23
Unfortunately for you, your experience echoes what I have found out over the years: MS Windows utilities work best with MS Windows filesystems; Linux utilities work best with Linux filesystems.

If you have access to anther PC, one running MS Windows, which can burn a CD, then look into downloading Partition Wizard.  It's a free MS Windows partitioning app, and since it understands MS Windows filesystems, it may be able to repair the partition problem.

If you find that does not work, you could also try EASEUS Partition Master -- same deal: free MS Windows partitioning app you burn to CD.

---

### Post by ahallubuntu on 2012-04-23
I've actually never had a problem resizing a Windows partition with Gparted and I've done it numerous times.  However, I always caution people who might do so to backup their data just in case, as there's always a chance something could go wrong during a partition resize, as the OP has learned.

I would use the Windows partition resizing tools if they are convenient, but if not, I still trust Gparted - but backup first if the data is important.

---

### Post by evanzo23 on 2012-04-28
Ah, thank you all for your responses! I wasn't able to post my reply considering how busy this week has been, but I was able to fix my computer partitioning this week. I ended up being able to recover the drive with cfdisk, but the way I did so escapes me now because it was a while ago. Once again, thanks for the help, and I already have made some backups ;)

---

