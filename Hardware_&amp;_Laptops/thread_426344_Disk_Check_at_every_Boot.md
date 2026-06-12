---
title: "Disk Check at every Boot"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by viz_e on 2007-04-28
Hi,
I installed edgy (a couple of months ago) and feisty on a acer aspire 1681WLMi. I have an issue that is present in both versions.

The disk is checked at every start-up of the system. Of course this takes time. Why is this so?

I hope that it is not an issue of the disk: in fact the analysis, partition check and so on took a lot of time during the installation process. I guess that this is what happens between steps 3 and 4 of the installation wizard. How can I check this out?

Thank you! :KS

---

### Post by hardyn on 2007-04-28
it sounds like it might be a problem with the hard disk.

just about every hard disk manuf. has a disk veryify tool, they are generally not drive specific, try one out.

---

### Post by josephus on 2007-04-28
you need to make a change to /etc/fstab

basically the sixth field (fs passno) for each device controls whether or not fsck is run for a particular partition.

For example here is part of my /etc/fstab (slightly edited so things fit on one line)
```

# /dev/hda6
UUID=xxxx   /    ext3   defaults,errors=remount-ro         0        1
# /dev/hda1
UUID=yyyy  /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46      0       0
```

/dev/hda6 this is my root partition and the sixth field should be set to 1
/dev/hda1 contains my windows stuff the sixth field is by default set to 2, which tells to fsck to scan the drive. Setting it to zero causes fsck to skip the partition.

This information is detailed in the man pages.

---

### Post by viz_e on 2007-04-29
Isn't that dangerous to prevent the disk check?

---

### Post by josephus on 2007-04-29
isn't that what you are trying to do?  or are you just asking a general question as to why it takes so long?

---

### Post by viz_e on 2007-04-29
I would like to understand why it needs to do it at every boot and if this is a sign that something is wrong (which should be clear, but how bad is it?)

---

### Post by viz_e on 2007-05-02
Any other ideas or anyone else with the same issue?

---

### Post by josephus on 2007-05-02
it's checks every time because you are telling it to.  it doesn't have to check every time if you don't want to.

---

### Post by viz_e on 2007-05-02
> **josephus said:**
> it's checks every time because you are telling it to.  it doesn't have to check every time if you don't want to.

That's a fresh install without changing settings... The same installation on two other machines are fine with this respect.

---

### Post by josephus on 2007-05-02
it's the default setting.  on the ext3 partition it checks every 30 times the drive is mounted, on things like fat32 and ntfs it checks every boot.

---

### Post by viz_e on 2007-05-02
> **josephus said:**
> it's the default setting.  on the ext3 partition it checks every 30 times the drive is mounted, on things like fat32 and ntfs it checks every boot.

Funny.I have ntfs e fat32 partitions even on the other notebooks.,,

How do I prevent this to happen?

---

### Post by josephus on 2007-05-02
are all your systems running feisty?

---

### Post by josephus on 2007-05-02
and read my first post.

---

### Post by viz_e on 2007-05-02
> **josephus said:**
> are all your systems running feisty?

Yes. On this particular notebook I already had the problem with edgy ( I don't know about dapper), but I didn't care.

---

### Post by josephus on 2007-05-02
i'm a little bit confused?  are you saying that your other notebooks running feisty don't check at each boot.

---

### Post by Docter on 2007-05-02
I've had a problem with fsck since edgy to the point where I've had to disable it completely.

If I leave the fsck field in fstab to any non-zero value at the next boot I'm kicked to a maintenance shell and I get errors of not being able to find bash commands like "apt-get". Leading to lovely error messages such as:
```

Cannot find apt-get. Try *apt-get apt* at the command line
```

That's very windoze. I'm told to run fsck manually in read-only mode although it seems to think that the superblock is set wrong. I've set it to likely values on several occasions with no joy and so I am forced to disable the automatic checking and instead do a disk check from the livecd periodically... if I can be bothered.

Cutting to the point this prevents my OS from loading and I need to mount my harddrive from the livecd to edit my fstab in order to regain access to my computer by disabling the filesystem check. 

I can't say it's an annoying problem as I completely ignore it and it has  yet to destroy the world... so hmm, yeah.

---

### Post by viz_e on 2007-05-02
> **josephus said:**
> i'm a little bit confused?  are you saying that your other notebooks running feisty don't check at each boot.

Yes. Only by this particular notebook, I loose the bootsplash during boot and checks the partitions (I cannot tell which one right now...). This happens by every boot and only on this notebook. For the other notebooks I get the usual check every 30 boots or one month (I think).

For this notebook it took much time to do the analysis of the disk during the installation process. (even though the disk was already partitioned for kubuntu).

---

### Post by josephus on 2007-05-02
i'm not sure why they were configured differently, but i'm pretty sure if you compare fstab on your different computers you'll see that difference is in the final field.

---

### Post by viz_e on 2007-05-02
> **josephus said:**
> i'm not sure why they were configured differently, but i'm pretty sure if you compare fstab on your different computers you'll see that difference is in the final field.

I cannot check right now, but isn't that the last column is either 0 or 1? (depending whether you allow or not the disk check?). If this is true I cannot really change the frequency.

---

### Post by josephus on 2007-05-02
from man fstab
0 - never check
1 - root file system
2 - other file systems

you can't change the frequency of checking fat32,ntfs partitions.  the reason for this is that there is no area on these partitions that is set up to store when the partition was last checked, therefore it just checks it everytime. for ext32 i think you change the frequency that it is checked.

---

### Post by viz_e on 2007-05-02
This is the portion of fstab for a FAT32 and NTFS driver of a correct working notebook:

# /dev/sda1
UUID=2E600CAF600C7FB7 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4395-E09D  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1

The "1" at the end should then mean to check at every boot. If this happens indeed, the bootsplash does not exit. It exits however, when it wants to check the home or root partition.

Thank you very much for the effort!

---

### Post by josephus on 2007-05-02
if that is from your notebooks that doesn't check every time, then i don't know what is causing the difference.

anyway you can read more about it on this bug report:

[https://bugs.launchpad.net/ubuntu/+source/dosfstools/+bug/59293](https://bugs.launchpad.net/ubuntu/+source/dosfstools/+bug/59293)

---

### Post by viz_e on 2007-05-02
Too bad that I don't remember which partition of the disk is continuously checked. I have to check it and see whether it is the fat or ntfs one...

---

### Post by headphase on 2007-05-03
I am having a similar problem getting an error on every check. Here is my log:
```
Log of fsck -C -R -A -a 
Thu May  3 08:54:28 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 85 files, 3926/20017 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda3: 41 files, 963111/1214546 clusters
/dev/sda6 contains a file system with errors, check forced.
/dev/sda6: Inode 5652487 has illegal block(s).  

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Thu May  3 08:55:47 2007
----------------
```

---

### Post by viz_e on 2007-05-06
Ok. Now I am using the notebook in question. This is what happens: by every boot, the boot splash exits and this part is displayed on the screen:

Log of fsck -C -R -A -a
Sun May  6 16:54:38 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 819 files, 360668/511061 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda2: 124384 files, 1434998/1761770 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda5: 28024 files, 1007572/1144265 clusters
/dev/sda7: clean, 1062/513024 files, 247192/1024135 blocks

(taken from /var/log/fsck/checkfs.

Actually when the bootsplash exits, the scan of sda1 is already finished. What it taking so long is the scan of sda2 (which is a fat32 partition hosting windows xp).

This is my /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=a33536f5-b697-4ae8-a495-f6fc98d5f80a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=ae04f1bf-82bc-4553-89ad-822f8152df9d /home           ext3    defaults        0       2
# /dev/sda1
UUID=3007-17F2  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2629-16F0  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=351B-160B  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=3f501a2e-f13d-4bf4-848b-5ae0a8a67007 none            swap    sw  

Anyone? Thanks!

---

### Post by viz_e on 2007-05-13
Anyone? Thx

---

### Post by Mr. Brownstone on 2007-05-28
Change this part of your fstab:```
# /dev/sda1
UUID=3007-17F2 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2
UUID=2629-16F0 /media/sda2 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=351B-160B /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
```To this:```

# /dev/sda1
UUID=3007-17F2 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 [color=#ff0000]**0**[/color]
# /dev/sda2
UUID=2629-16F0 /media/sda2 vfat defaults,utf8,umask=007,gid=46 0 [color=#ff0000]**0**[/color]
# /dev/sda5
UUID=351B-160B /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 [color=#ff0000]**0**[/color]
```Make sure you edit fstab with "sudo nano -w /etc/fstab"

Reboot to see if it worked.

---

