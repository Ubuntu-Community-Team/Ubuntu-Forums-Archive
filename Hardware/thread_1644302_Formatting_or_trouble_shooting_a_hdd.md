---
title: "Formatting or trouble shooting a hdd"
date: 2010-12-13
forum: Hardware
---

### Post by Garthhh on 2010-12-13
I working on this vaio vgn-nw350f laptop. 
I was setting up a dualboot & it kept acting worse & worse,  slow, freezes... 
I messed around with the partitions in gparted,  
finally it wouldn'd start windows7 at all, so I tried to install mint on  the whole HDD, still no luck [gets stuck on formatting the partitions 
I'm running lucid puppy version 5.0 off a 8gb flash drive 
I tried to format the hdd using  
Gparted 
 
[B]GParted 0.5.1 
 
Libparted 2.2 
Create Primary Partition #1 (ext2, 298.09 GiB) on /dev/sda  00:01:41    (  ERROR ) 
          
create empty partition  00:00:00    ( SUCCESS ) 
          
path: /dev/sda1 
start: 63 
end: 625137344 
size: 625137282 (298.09 GiB) 
set partition type on /dev/sda1  00:00:01    ( SUCCESS ) 
          
new partition type: ext2 
create new ext2 file system  00:01:40    ( ERROR ) 
          
mkfs.ext2 -L "" /dev/sda1 
          
Filesystem label= 
OS type: Linux 
Block size=4096 (log=2) 
Fragment size=4096 (log=2) 
Stride=0 blocks, Stripe width=0 blocks 
19537920 inodes, 78142160 blocks 
3907108 blocks (5.00%) reserved for the super user 
First data block=0 
Maximum filesystem blocks=0 
2385 block groups 
32768 blocks per group, 32768 fragments per group 
8192 inodes per group 
Superblock backups stored on blocks: 
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
4096000, 7962624, 11239424, 20480000, 23887872, 71663616 
 
Writing inode tables: done 
mke2fs 1.41.11 (14-Mar-2010) 
ext2fs_mkdir: Attempt to read block from filesystem resulted in short  read while creating root dir

[/B]I also tried 
[http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html)
with similar results****I found this
[http://ubuntuforums.org/showthread.php?t=837867](http://ubuntuforums.org/showthread.php?t=837867)
I'm not quite sure how to bite off a smaller chunk to format
or even to determine if it is a terminal hardware problem****

---

