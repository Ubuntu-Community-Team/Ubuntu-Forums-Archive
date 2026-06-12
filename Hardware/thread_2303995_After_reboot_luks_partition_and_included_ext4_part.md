---
title: "After reboot luks partition and included ext4 part missing"
date: 2015-11-23
forum: Hardware
---

### Post by diagpope on 2015-11-23
Hi,

I have been researching a lot of sites and found some good advice but am still looking for the final solution for this problem:

In my ubuntu 14.04 install I have one raid 5 setup of 3 drives. On this device md0 I have setup one luks parttion. Its mapper md0 then is formatted as ext4.
Recently I rebooted and the luks id was missing in blkid output. 
I started searching for advise:

Here is status of the raid. All logs from that day do not indicate any faulure of the raid before or after the poweroff.

 cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sda1[3] sdc1[0] sdd1[1]
      5860267008 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

BTW: This is the expected blkid from my records

# expected luksid
md0 99d8dff5-d660-459d-b055-249d24db0430 < luksid

The first hint I found online was grepping for the LUKS header on the device
sudo hexdump -C /dev/md0 | grep LUKS
00080000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|

So there is a LUKS header there at an offset of 0x00080000

=> This is not expected as al my luks partitions usually start at offset zero. Hmm, 

So the next step is to open this luks part.

losetup -o 0x00080000 -r -f /dev/md0
losetup -a
/dev/loop0: [0005]:13409 (/dev/md0), offset 524288

cryptsetup luksOpen /dev/loop0 luksrecover
Enter passphrase for /dev/md0: 

Up to here I am still happy...

Then I expect this mapper to be formatted ext4 with data on it:

 mount -o ro /dev/mapper/luksrecover /mnt/recover
mount: you must specify the filesystem type
-- /root --
[root@intel]# mount -t ext4 -o ro /dev/mapper/luksrecover /mnt/recover
mount: wrong fs type, bad option, bad superblock on /dev/mapper/luksrecover,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So we know there is not valid filesystem - disappointment ..

The luks device info is:

cryptsetup status luksrecover
/dev/mapper/luksrecover is active.
  type:    LUKS1
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/loop0
  loop:    /dev/md0
  offset:  4096 sectors
  size:    11720528896 sectors
  mode:    readonly

#actual luksid
cryptsetup luksUUID /dev/loop0 
92ce3494-636b-4735-b6f0-3567f16e5ae0

Here we wonder: Why is this luksid different from the one I was expecting?


So I started testdisk hoping to find the ext4 filesystem as they should not be a partition table (please do not ask why I chose not to use part table, I do not know)

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/mapper/luksrecover - 6000 GB / 5588 GiB - 11720528896 sectors (RO)

The harddisk (6000 GB / 5588 GiB) seems too small! (< 15948711 TB / 14505268 TiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  MS Data               2282375229 26542910664190148 26542908381814919 [ M-M&&#306;9~J^^]
   MS Data               3056653794 10458979889280326 10458976832626532 [^EM-Q:^C  ~IgC]
   MS Data               6156373845 30059849993476755 30059843837102910 [^G
   MS Data               7902647472 31149826686305011 31149818783657539 [i^U ^RM-;(k
   MS Data               10414709388 6273487744292990 6273477329583602 [T ^G <U+0376>M- 3]
   MS Data               10747092536 3168699173102149 3168688426009613 [~Y ^XM-[M-e&#1939;M-&^^]

Well all this does not look familiar to me and I can not find the ext4 file system

As I may be at a loss of finding the data I would still like to know
1) Has anybody ever experienced the loss of a LUKS partition w/o any obvious user mistake ? 
- I did a clean poweroff 
2) Could it be possible to find the ext format if I resize the luks to move down its offset back to zero ?
3) How can there be an offset ?
- I assume there was never one prior but I can not prove this as I have no luks header backup

Any comments is appreciated

---

