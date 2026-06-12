---
title: "RAID 1 mucked up by hosting company"
date: 2013-03-27
forum: Hardware
---

### Post by terry1738 on 2013-03-27
Good Day I have a hosted server which I accidently got locked out of and the guy at hosting company tried to fix for me but made the server un bootable.
I have little (but rapidly gaining  knowledge) of RAID 1 .
I had previously fixed the problem I had on sdb2 by moving a directory so sda2 and sdb2 now have different data but the system still booted ignoring the changes I made to sdb2 my intention was to mount sdb2 and rewrite sda2 but I offered to pay them to do that because of my lack of knowledge in raid speak and thats when they took over the fix.
They have a ubuntu shell to log in to for recovery and thankfully I can mount all the disks and see the data on all the disks so I am not completly lost
When I logged into the shell I did this to see if I had data

mdadm -A -R /dev/md0 /dev/sda1
mount /dev/md0 /mnt
la /mnt
umount /mnt
mdadm -S /dev/md0

mdadm -A -R /dev/md1 /dev/sda2
mount /dev/md1 /mnt
la /mnt
umount /mnt
mdadm -S /dev/md1

mdadm -A -R /dev/md0 /dev/sdb1
mount /dev/md0 /mnt
la /mnt
umount /mnt
mdadm -S /dev/md0

mdadm -A -R /dev/md1 /dev/sda2
mount /dev/md1 /mnt
la /mnt
umount /mnt
mdadm -S /dev/md1


then fdisk -l showed
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035512

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1044224      522081   fd  Linux raid autodetect
/dev/sda2         1044225  1951415549   975185662+  fd  Linux raid autodetect
/dev/sda3      1951415550  1953520064     1052257+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00077abd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1044224      522081   fd  Linux raid autodetect
/dev/sdb2         1044225  1951415549   975185662+  fd  Linux raid autodetect
/dev/sdb3      1951415550  1953520064     1052257+  82  Linux swap / Solaris

Disk /dev/md1: 998.6 GB, 998589988864 bytes
2 heads, 4 sectors/track, 243796384 cylinders, total 1950371072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Then cat /proc/mdstat 
Personalities : [raid1] [raid0] [raid6] [raid5] [raid4] 
md1 : active raid1 sdb2[1]
      975185536 blocks [2/1] [_U]
      unused devices: <none>

Then I ran
mdadm -A --scan
mdadm: ignoring /dev/sdb1 as it reports /dev/sda1 as failed
mdadm: /dev/md0 has been started with 1 drive (out of 2).
mdadm: /dev/md9 has been started with 1 drive (out of 2).

Then cat /proc/mdstat 
Personalities : [raid1] [raid0] [raid6] [raid5] [raid4] 
md0 : active raid1 sda1[0]
      521984 blocks [2/1] [U_]
      
md1 : active raid1 sdb2[1]
      975185536 blocks [2/1] [_U]
      
md9 : active raid1 sda2[0]
      975185536 blocks [2/1] [U_]
      

I rebooted at this stage but again the system would not boot so thats the extent of my knowledge and if I play around with it I will only make it worse so I am hoping some one can help.
I am putting the drive back into recovery so I can do some examines which I will post back.
 I can not say for sure what he did last night but I have a history of the commands he made below.

    1  cat /proc/mdstat 
    2  mdadm --assemble --run /dev/md1
    3  mdadm --assemble --run /dev/md1 /dev/sdb2
    4  cat /proc/mdstat 
    5  mount /dev/md1 /mnt
    6  ls /mnt
    7  ls /mnt/root -a
    8  ls /mnt/root/.ssh -lda
    9  cat /proc/mdstat 
   10  exit
   11  fdisk -l
   12  cat /proc/mdstat 
   13  watch -n5 cat /proc/mdstat 
   14  cat /proc/mdstat 
   15  fdisk -l
   16  mdadm --assemble --run /dev/md0
   17  mdadm --assemble --run /dev/md1
   18  mdadm --assemble --run /dev/md2
   19  la /mnt/
   20  mdadm --examine /dev/sda2
   21  mdadm --examine /dev/sdb2
   22  mdadm -a /dev/md1 /dev/sda2 
   23  mdadm --examine /dev/sdb2

---

### Post by terry1738 on 2013-03-27
First update ITS WORKING HOORAY seems I work for 30 hours make a post for help then I fix it. But there is a bit more to do so I wont open the champers just yet
when I do
cat /proc/mdstat 
Personalities : [raid1] 
md9 : active raid1 sda2[0]
      975185536 blocks [2/1] [U_]
      
md0 : active raid1 sda1[0]
      521984 blocks [2/1] [U_]
      
md1 : active raid1 sdb2[1]
      975185536 blocks [2/1] [_U]
      
unused devices: <none>

So mdadm -A --scan got it right NOW how do I fix it so i have the raid array back is the next problem. Any help would be fantastic as I am up that creek at the moment.

---

### Post by SaturnusDJ on 2013-03-28
I assume you had two raid1 array: sd[a-b]1 and sd[a-b]2.

Now you've to choose one member of each array to start with. This member would be the disk containing the partition that's still up-to-date/healthy.
The other member, probably outdated or unhealthy, most likely still has a superblock. In order to prevent accidents, clear this superblock with the mdadm zero-superblock function. Be aware that you do not clear the superblock of the healthy member!!

Now start the arrays degraded containing one healthy member. Then add the member that you just gave a superblock erase. Resync/recovery starts, and afterwards you're running a healthy raid1 array.

---

