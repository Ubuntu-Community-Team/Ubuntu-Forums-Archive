---
title: "Mounting ntfs software raid trouble"
date: 2008-10-16
forum: General Help
---

### Post by emir0n on 2008-10-16
Hi

I have a problem mounting my ntfs software raid in ubuntu.I have 3 disks :

root@eniac:~# cat /proc/partitions 
major minor  #blocks  name

   8     0   80043264 sda
   8     1   79011840 sda1
   8     2    1023958 sda2
   8    16   80043264 sdb
   8    17   79011840 sdb1
   8    18    1023958 sdb2
   8    32   80043264 sdc
   8    33   28314531 sdc1
   8    34    9767520 sdc2
   8    35   39062047 sdc3
   8    36    2891700 sdc4

sda1 and sdb1 are my two ntfs partitions merged in windows (stripping mode).sdc1 is my windows system partition (automaticly mounted after instalation).sdc2,3,4 are my linux partitions
i alredy searched for some guides : 

[http://ubuntuforums.org/showthread.php?t=833653](http://ubuntuforums.org/showthread.php?t=833653)

after trying to mount the array an error showed up : 

root@eniac:~# mount -t ntfs /dev/md0 /media/decko/$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/md0': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

now i rly dont know what to do/try next ... anyone that could throw me a bone ? :)

---

### Post by fjgaude on 2008-10-16
The software you setup in Windows is not something Ubuntu can read. Your /md0 array hasn't been made.

You might look into a program called **dmraid**. That might work to mount your ntfs array.

---

### Post by emir0n on 2008-10-16
> **fjgaude said:**
> The software you setup in Windows is not something Ubuntu can read. Your /md0 array hasn't been made.

You might look into a program called **dmraid**. That might work to mount your ntfs array.

well i made the raid with windows and i tried to run dmraid and activate the raid but he didnt detect any raid disks ...

---

### Post by fjgaude on 2008-10-16
The more I think about it the more I believe there is nothing in Linux that will mount a Windows made software array... the fakeRAID that is in BIOS of manmy modern motherboards can be handled with **dmraid**.

I have no other suggestion than to forget being able to do this. Make an array in Ubuntu using **mdadm** or make an array with your BIOS and then use dmraid to mount it.

I trust you have backups to all important data. I keep three sets, one online, near-line, and off-line.

---

### Post by emir0n on 2008-10-18
> **fjgaude said:**
> The more I think about it the more I believe there is nothing in Linux that will mount a Windows made software array... the fakeRAID that is in BIOS of manmy modern motherboards can be handled with **dmraid**.

I have no other suggestion than to forget being able to do this. Make an array in Ubuntu using **mdadm** or make an array with your BIOS and then use dmraid to mount it.

I trust you have backups to all important data. I keep three sets, one online, near-line, and off-line.

well i was afraid u will say that :( 
hm i have there 140 GB of data and about 20 GB of data that i really need - work,documents,photos etc ... i alredy have experience with the array creating,using and mouting a array created trough the bios utility,i alredy had it mounted in linux year ago and after PC reinstalation i tried the windows array ...

ok i will see what i will do,thx for the help anyway :)

---

### Post by Yugoo on 2008-10-20
hi, just did this one myself, so can you :)

~$ cat /proc/partitions

Will give you something like this:

major minor  #blocks  name

   8     0  244198584 sda
   8     1  238123431 sda1
   8     2          1 sda2
   8     5    6072538 sda5
   8    16  156250000 sdb
   8    17      64228 sdb1
   8    18  309267315 sdb2
   8    19    3148740 sdb3
   8    20       8032 sdb4
   8    32  156250000 sdc
 254     0  312495360 dm-0
 254     1      64228 dm-1
 254     2  309267315 dm-2
 254     3    3148740 dm-3
 254     4       8032 dm-4

You can now see which file system to mount by looking at the size of each one (look at the ones next to 254 and use the size of your windows drive. Subtract the size of your boot partition or any other where the file system you want is not located)

Do this next:

~$ sudo aptitude install dmraid

Then:

~$ sudo dmraid -ay

You will see something similar to this:

RAID set "isw_gfcgcccgg_ARRAY" already active
RAID set "isw_gfcgcccgg_ARRAY1" already active
RAID set "isw_gfcgcccgg_ARRAY2" already active
RAID set "isw_gfcgcccgg_ARRAY3" already active
RAID set "isw_gfcgcccgg_ARRAY4" already active

By looking at the partitions list you should be able to summise which one to use. In my case it was:

RAID set "isw_gfcgcccgg_ARRAY2" already active (look at the partitions list and you can tell which one you need)

Now do this:

~$ sudo mount -t ntfs-3g /dev/mapper/isw_gfcgcccgg_ARRAY2 /mnt/windriv 

This will mount the windows file system to the destination /mnt/windrive (you can call it whatever you like)

once you have mounted the drive you should create a script to run at startup so that it mounts automatically each time you start your OS. Check this out if you need help:

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Hope this helps. I find it useful to use 2 or 3 terminal windows at once so you can cross reference them

---

### Post by fjgaude on 2008-10-21
Question: does the software raid created by a Windows OS be covered with dmraid? Most fakeRAID created by BIOSs are covered, but I don't know about Windows-type software raid.

---

### Post by Yugoo on 2008-10-21
I believe so. My original setup was Windows raid0 (fake). It consisted of 2 150GB drives striped to 300GB. I then added a third SATA drive (they're all SATA by the way) to install Ubuntu on but found I could not mount the Wins file system for all the reasons found in this forum and elsewhere.

After dowloading dmraid and ntfs 3g, and then following the procedure above my wins files are now mounted

---

### Post by fjgaude on 2008-10-21
Yugoo, your fakeraid was created by your BIOS?

---

### Post by Yugoo on 2008-10-21
If I understand your question correctly, yes. It's a Dell machine which was sold to me with a striped set of two drives. Raid 0 which is by definition BIOS (fake)raid...

---

### Post by Yugoo on 2008-10-21
Frank, I was just looking at your setup. I guess the fundamental difference between what you and I have is that I have no parity. As I've never worked with raid 5 I don't know what this method would mean in your situation, but I suspect it is not the same. My stripe is of two and I'm not sure the device mapper can work with parity over three. Where were your questions leading?

---

### Post by Yugoo on 2008-10-21
Last post on this thread. My solution works only for mounting raid 0 stripe. Apologies for red herring if you have raid 5. dmraid will not work in this situation, but hope this post helps anyone with raid 0.

---

### Post by fjgaude on 2008-10-21
My situation, I run **mdadm** and raid5, don't need or use **dmraid**. Was just trying to understand others' needs. I run WinXP in VMware along with three or four Windows graphic design packages under Ubuntu.

Also I do think that some versions of Windows can create in the OS raid arrays. That's why some confusion.

---

### Post by emir0n on 2008-10-29
thx alot yugoo,i got it running using your manual and yea,the script is not a big deal :]

---

