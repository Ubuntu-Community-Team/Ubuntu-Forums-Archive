---
title: "Unrecognized mount option &quot;uid=1000&quot; error w/TrueCrypt 6.0a on Ubuntu 8.04.1 server"
date: 2008-10-13
forum: General Help
---

### Post by sampablokuper on 2008-10-13
Hi folks,

I've had some problems setting up TrueCrypt on RAID5. I've detailed the problem over on the TrueCrypt forums [[COLOR="Blue"]here[/COLOR]]("http://forums.truecrypt.org/viewtopic.php?t=13121") but haven't had a response there yet. As Ubuntuforums seems to be a bit more active, and since there are clearly other TrueCrypt users here, I hope someone here might be able to help out instead, or in addition.

It's a blocking problem for me - a number of other tasks depend on my getting this volume encrypted & mounted cleanly - which is why I'm keen to find resolution asap. I'm sorry if I sound impatient.

Many thanks for your help,

Sam

---

### Post by Pelham123 on 2008-10-14
Your link requires login and password to read. Can you detail problem here please ;)

---

### Post by sampablokuper on 2008-10-14
> Your link requires login and password to read. Can you detail problem here please

OK, here's a copy of my post on the TrueCrypt forum:

My system has the following storage devices: a USB drive with my system partitions on it, and four 500GB SATA drives I want to make into an encrypted RAID5 array. I used 
```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc /dev/sdd
```
to create the array, and then used the latest version of TrueCrypt (6.0a) to create an encrypted volume using the following command:
```
sudo truecrypt --text --filesystem=none --volume-type=normal --encryption=Serpent-Twofish-AES --hash=SHA-512 --random-source=/dev/urandom -c /dev/md0
```

This took 13 hours but seemed to work OK. 
I then issued the following commands: 
```
sudo truecrypt /dev/md0 --filesystem=none 
sudo truecrypt -l # This gave, '1: /dev/md0 /dev/mapper/truecrypt1 -' 
sudo mkfs.ext3 /dev/mapper/truecrypt1 
sudo mkdir /mnt/sataraid5 
sudo truecrypt --filesystem=ext3 /dev/md0 /mnt/sataraid5
```
All of these commands seemed to work except the final one, which gave the error, 'Unrecognized mount option "uid=1000" or missing value'. 

Can anyone see what (if anything) I'm doing wrong here? 

Many thanks in advance, 

spk 
-- 
HP ML110 G3 
Ubuntu 8.04.1 server LTS x64
TrueCrypt 6.0a for Ubuntu x64

---

### Post by sampablokuper on 2008-10-14
Even if no-one has a solution to this one, I'd be grateful to at least know if anyone else has experienced the same problem. I've tried rebooting a couple of times and it's still happening.

---

### Post by Pelham123 on 2008-10-14
Sorry for late reply. From what you have posted seems to make sense, but I have read a couple of posts that suggest adding the following line to your command list:

> **sampablokuper said:**
> 
 
I then issued the following commands: 
```
sudo truecrypt /dev/md0 --filesystem=none 
sudo truecrypt -l # This gave, '1: /dev/md0 /dev/mapper/truecrypt1 -' 
sudo mkfs.ext3 /dev/mapper/truecrypt1 
sudo mkdir /mnt/sataraid5 

**sudo truecrypt -d** ## as you know unmounts all TC volumes

sudo truecrypt --filesystem=ext3 /dev/md0 /mnt/sataraid5
```



*shrugs shoulders* :confused:

---

### Post by sampablokuper on 2008-10-14
> **Pelham123 said:**
> what you have posted seems to make sense, but I have read a couple of posts that suggest adding the following line to your command list
Thanks for the suggestion, but unmounting doesn't help. When I mount again, I get the same error.

I'm struggling to understand the error, as this is the first time I've set up RAID on Ubuntu, and also the first time I've used TrueCrypt on Ubuntu.

So far, my research has turned up the following information:
[LIST]
[*]"[[COLOR="Blue"]uid 1000 is supposedly your own user uid[/COLOR]]("http://kubuntuforums.net/forums/index.php?topic=3097130.0")". This at least explains something about UID=1000 that I didn't know.
[*]It might help if I provide the output of certain tests on my system.
[/LIST]
On the latter point,
```
sudo truecrypt -d
sudo fsck /dev/md0
```
gives the following:
```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
which I *think* is correct (because I don't recall creating an ext2 filesystem on /ext/md0), and
```
sudo mdadm --stop /dev/md0
```
works fine, as does
```
sudo mdadm --assemble --scan
```.
```
cat /proc/mdstat
```
gives:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sda[0] sdd[3] sdc[2] sdb[1]
      1465159488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
unused devices: <none>
```
which I think is OK too.

I don't have any entries for /dev/md0 or for /mnt/sataraid5 in my /etc/fstab, which if I'm not mistaken is also unproblematic.

The only command I've tried (other than the one this thread is about) that gives me cause for concern is
```
sudo fdisk -l
```
which gives (I've abbreviated the output):
```
Disk /dev/sda doesn't contain a valid partition table
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdc doesn't contain a valid partition table
Disk /dev/sdd doesn't contain a valid partition table
Disk /dev/md0 doesn't contain a valid partition table
```.
I don't know if that's as it should be, given the set-up I outlined above.

In summary, I've done a fair bit of homework since my last post, but I'm still not much closer to solving the 'Unrecognized mount option "uid=1000" or missing value' problem.

All help greatly apprectiated,

Spk

---

### Post by sampablokuper on 2008-10-14
It occurred to me it might also help for me to list the output of a couple of other commands:
```
sampablokuper@server:~$ sudo truecrypt --filesystem=ext3 /dev/md0 /mnt/sataraid5
[19059.398715] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

sampablokuper@server:~$ sudo fsck /dev/md0
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/md0
Filesystem mounted or opened exclusively by another program?

sampablokuper@server:~$ sudo fsck /mnt/sataraid5/
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Is a directory while trying to open /mnt/sataraid5/
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
Of course, the first command above gives the same error as mentioned at the beginning of this thread. Not sure if the rest of the above gives any further insight into my problem, but I hope it does!

I look forward to hearing your suggestions :)

Spk

---

### Post by sampablokuper on 2008-10-14
One more piece of output which might help get to the bottom of this:
```
sampablokuper@server:~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=eb6bae73:95ac00ca:23e4bfe4:54d32271

# This file was auto-generated on Sun, 12 Oct 2008 22:31:13 +0100
# by mkconf $Id$
```

---

### Post by sampablokuper on 2008-10-15
I've had a reply on the TrueCrypt forum. I won't quote it in full (because the copyright obviously belongs to the person who wrote it), but I will quote part of it:

> Truecrypt first tries to mount the volume with the mount option uid=<current-user-id> just to make a FAT/NTFS volume working right. Since you are using ext3, the above option makes no sense and it is rejected by mount.ext3, so truecrypt retries the mount *without* that option and this time it should succeed.

In other words, as long as the mounted encrypted volume *works*, the error message can be ignored.

It seems to me that TrueCrypt oughtn't to give the user an error message in this case, but I'm grateful to the person who explained to me what was happening.

---

### Post by Pelham123 on 2008-10-16
Thanks for the update.

I must admit I found a few similar posts that required uid parameters to be added to FAT filesystems (and that would therefore give the uid error) but as you were applying an ext3 filesystem and no -u switch to the partition, it didnt make sense.

Hopefully its working for you though ;)

---

### Post by sampablokuper on 2008-10-19
Yep, it's working. Thanks for following the thread!

---

