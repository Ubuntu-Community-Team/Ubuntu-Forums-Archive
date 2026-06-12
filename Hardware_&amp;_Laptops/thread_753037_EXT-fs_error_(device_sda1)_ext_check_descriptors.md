---
title: "EXT-fs error (device sda1): ext_check_descriptors"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by igorj_v on 2008-04-12
experimenting with notebook ; forgot to charge batery ; leaved notebook for an hour; 
ofcourse batery discharged ; after charging batery ; trying to turn on notebook it started in BusyBox; 

when started notebook with live cd
 in log file found error like ("in console typed" dmesg | tail "by root") 

EXT-fs error (device sda1): ext_check_descriptors: Block bitmap for group 512 not in group (block 0)
EXT-fs: group descriptors corupted

laptop has only one HDD disk SAMSUNG 160Gb 

how to solve error using ubuntu comands (help in BusyBox gave a lot of comands ; but still little understanding what comand to use )

---

### Post by igorj_v on 2008-04-12
testdisk gives such log

TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63

     Partition                  Start        End    Size in sectors

  Linux                    0   1  1 18700 254 57  300431496
superblock 0, blocksize=4096
superblock 32768, blocksize=4096
superblock 98304, blocksize=4096
superblock 163840, blocksize=4096
superblock 229376, blocksize=4096
superblock 294912, blocksize=4096
superblock 819200, blocksize=4096
superblock 884736, blocksize=4096
superblock 1605632, blocksize=4096
superblock 2654208, blocksize=4096

as writen in help using values from superblock in console fulfill

root@ubuntu:/home/ubuntu# /sbin/fsck.ext3 -b 98304 -B 4096 /dev/sda 
e2fsck 1.40.2 (12-Jul-2007)
/sbin/fsck.ext3: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
root@ubuntu:/home/ubuntu# 


how it is ; if there is no another program reading ( may be live cd ):(
also trying to mount disk it says 

Unable to mount the volume.

wait 


forgot instead of /dev/sda for hdd disk used /dev/sda1

root@ubuntu:/home/ubuntu/Videos# /sbin/fsck.ext3 -b 98304 -B 4096 /dev/sda1
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
 
 so waiting

---

### Post by igorj_v on 2008-04-12
a lot of such rows 

Fix<y>? yes

Free inodes count wrong for group #753 (16384, counted=16383).
Fix<y>? yes

Directories count wrong for group #753 (0, counted=1).
Fix<y>? yes

Free inodes count wrong for group #834 (16384, counted=16379).
Fix<y>? yes

Free inodes count wrong for group #848 (16384, counted=16383).
Fix<y>? yes

Free inodes count wrong for group #849 (16384, counted=16375).
Fix<y>? yes

Free inodes count wrong for group #863 (16384, counted=16383).
Fix<y>? yes

Free inodes count wrong for group #873 (16384, counted=16383).
Fix<y>? yes

Free inodes count wrong for group #900 (16384, counted=16341).
Fix<y>? yes

Free inodes count wrong for group #902 (16384, counted=16373).
Fix<y>? yes

Free inodes count wrong for group #903 (16384, counted=16163).
Fix<y>? yes

Free inodes count wrong for group #905 (16384, counted=16383).
Fix<y>? yes

Free inodes count wrong for group #925 (16384, counted=16278).
Fix<y>? yes

Directories count wrong for group #925 (0, counted=14).
Fix<y>? yes

Free inodes count wrong for group #1012 (16384, counted=14996).
Fix<y>? yes

Directories count wrong for group #1012 (0, counted=118).
Fix<y>? yes

Free inodes count wrong for group #1013 (16384, counted=14879).
Fix<y>? yes

Directories count wrong for group #1013 (0, counted=470).
Fix<y>? yes

Free inodes count wrong for group #1014 (16384, counted=15394).
Fix<y>? yes

Directories count wrong for group #1014 (0, counted=180).
Fix<y>? yes

Free inodes count wrong for group #1015 (16384, counted=15999).
Fix<y>? yes

Directories count wrong for group #1015 (0, counted=91).
Fix<y>? yes

Free inodes count wrong for group #1016 (16384, counted=16353).
Fix<y>? yes

Directories count wrong for group #1016 (0, counted=11).
Fix<y>? yes

Free inodes count wrong for group #1047 (16384, counted=16376).
Fix<y>? yes

Directories count wrong for group #1047 (0, counted=4).
Fix<y>? yes

Free inodes count wrong for group #1050 (16384, counted=16065).
Fix<y>? yes

Directories count wrong for group #1050 (0, counted=115).
Fix<y>? yes

Free inodes count wrong for group #1051 (16384, counted=16313).
Fix<y>? yes

Directories count wrong for group #1051 (0, counted=1).
Fix<y>? yes

Free inodes count wrong for group #1057 (16384, counted=16383).
Fix<y>? yes

Free inodes count wrong for group #1077 (16384, counted=16375).
Fix<y>? yes

Directories count wrong for group #1077 (0, counted=2).
Fix<y>? yes

Free inodes count wrong for group #1110 (16384, counted=16383).
Fix<y>? yes

Directories count wrong for group #1110 (0, counted=1).
Fix<y>? yes

Free inodes count wrong for group #1124 (16384, counted=16381).
Fix<y>? yes

Directories count wrong for group #1124 (0, counted=1).
Fix<y>? yes

Free inodes count wrong for group #1136 (16384, counted=15814).
Fix<y>? yes

Directories count wrong for group #1136 (0, counted=51).
Fix<y>? yes

Free inodes count wrong for group #1137 (16384, counted=15722).
Fix<y>? yes

Directories count wrong for group #1137 (0, counted=358).
Fix<y>? yes

Free inodes count wrong for group #1138 (16384, counted=12116).
Fix<y>? yes

Directories count wrong for group #1138 (0, counted=584).
Fix<y>? yes

Free inodes count wrong for group #1139 (16384, counted=16378).
Fix<y>? yes

Directories count wrong for group #1139 (0, counted=4).
Fix<y>? yes

Free inodes count wrong for group #1140 (16384, counted=15897).
Fix<y>? yes

Directories count wrong for group #1140 (0, counted=34).
Fix<y>? yes

Free inodes count wrong for group #1141 (16384, counted=15961).
Fix<y>? yes

Directories count wrong for group #1141 (0, counted=44).
Fix<y>? yes

Free inodes count wrong for group #1142 (16384, counted=16248).
Fix<y>? yes

Directories count wrong for group #1142 (0, counted=35).
Fix<y>? yes

Free inodes count wrong (18792437, counted=18596002).
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 196446/18792448 files (1.1% non-contiguous), 8452091/37553937 blocks

---

### Post by igorj_v on 2008-04-12
hdd is mounted ; restarting

---

