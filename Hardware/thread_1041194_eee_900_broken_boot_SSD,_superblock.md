---
title: "eee 900 broken boot SSD, superblock"
date: 2009-01-16
forum: Hardware
---

### Post by dinodeman on 2009-01-16
Hi guys,

This is the first time I have to post on this forum, because most of the time I can fix it myself. But this is the first time I can't do it myself or find the correct solution on the internet for me. So I'm in dire need of your help guys.

I have a EEE 900 with "ubuntu eee" installed on it, but it somehow happend that after a month I got this fault while startup (during the disk check) that something was wrong and I needed to fix my harddrive. So I used fsck as recommended and it started rewriting my inodes. After that everything worked as a charm. The following day I rebooted and again he needed me to fix my harddrive. So I ran fsck again with succes, but after reboot I got a Grub 17 error. So I got my Live USB stick and booted up.

My first move was to recover my boot disk, with tools like testdisk and fsck, but without succes. I used this [this]("https://help.ubuntu.com/community/DataRecovery") guide to fix my filesystem or recover some of the data.

So I said to myself, f**k the data on my boot partition. I can still get to my secondairy harddrive to work with the live usb disk so most important data is saved.

I decided let's reinstall ubuntu eee, but it failed during the installation. It gave me a error on 5% during the creation of ext3 file system. The error was:
> 
The ext3 file system creation in partition #1 of SCSI2 (0,0,0)(sda) failed.

I googled the error and found out that I need to add update-dev to /lib/partman/commit.d/30parted. Found the solution  [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908"). Then I restarted the installation, but I still got the same error on install. So I looked if I could maybe manualy format it with partition tools, but somehow it cannot find the disk. While the ubuntu installation can.

So it was something else that bugged my installation of ubuntu eee. I first tried to command fdisk -l /dev/sda, but this gave me the following message:
> 
Cannot open /dev/sda

/dev/sda is my primary disk.

Then I tried to see if the drive exists. I used the command cat /proc/partitions. This gave me the following output:
> 
major minor #blocks name
8 0 3940272 sda
8 16 15761088 sdb
8 17 15759733 sdb1
8 32 1007615 sdc
8 33 1007584 sdc1
7 0 862144 loop0


So my first drive is there, but somehow not accessible.

Then I tried to mount the disk with the command.
sudo mount -t ext3 /dev/sda /media/disk2
But the result was not good, it gave me the following error:
> 
mount: wrong fs type, bad option, bad superblock on /dev/sda, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so.

And here is the output of dmesg | tail:
> 
[ 6726.080026] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 6726.080026] sd 1:0:0:0: [sda] 7880544 512-byte hardware sectors (4035 MB)
[ 6726.080026] sd 1:0:0:0: [sda] Write Protect is off
[ 6726.080026] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6726.080026] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 6726.080026] sd 1:0:1:0: [sdb] 31522176 512-byte hardware sectors (16139 MB)
[ 6726.080026] sd 1:0:1:0: [sdb] Write Protect is off
[ 6726.080026] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 6726.080026] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 6726.080026] EXT3-fs: unable to read superblock

The superblock is broken and I needed one of the backup superblocks to replace my original. Simple fix I thought just type "dumpe2fs /dev/sda | grep -i superblock" to find a backup superblock. I thought wrong and I got an error:
> 
dumpe2fs 1.41.3 (12-Oct-2008
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Couldn't find valid filesystem superblock.


Some other commands I used to fix or find out what this mess is all about, with there output.

sudo fsck -V -t ext3 /dev/sda
> 
fsck 1.41.3 (12-Oct-2008)
[/sbin/fsck.ext3 (1) -- /dev/sda] fsck.ext3 /dev/sda
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Could this be a zero-length partition?


sudo mount -t ext3 -o bs=8193,error=continue /dev/sda /media/prim
> 
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



sudo e2fsck -b 8193 /dev/sda
> 
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


So what I concluded is that I cannot backup any of my data and I cannot reinstall ubuntu on the harddrive. This means my primary harddrive has become useless. I hope some of you know what I can do to get the install working. I just ran out of idees to fix this problem.

---

### Post by dinodeman on 2009-01-16
May my problem be caused by a hardware failure of the SSD drive? I have been extra carefull with it. I put allmost everything to ram like my firefox cache and all temporary directory. When I downloaded something I wrote this to the temp dir and then installed it so the installation files never saw my actual harddrive.

I'm thinking about sending it back to the store or Asus.

---

### Post by RJARRRPCGP on 2009-01-16
Looks like a bad disk drive.

---

### Post by bkortleven on 2009-05-08
for what it is still worth, I had the exact same troubles with my EEE 900.
I sent it over for repairs to Asus, and they shipped it to a repair center.
There they told me that the keyboard was broken, because of me spilling water or some other fluid into the machine...??? I had to pay € 260 excluding VAT to have it repaired and sent back, or € 70 to have it sent back in this state, or the exact same amount to trash it and dispose of it there. This is, by the way, the fourth machine with hardware issues I know that was sent back, with troubles of repair or cashback, within the first year of usage...


Coverup of a problem with the Onboard SSD', trying to make it a 'the user messed up' problem?
I'm fed up with these things, and I sent the story to my lawyer who is trying to get my money back. Shame on you Asus!!! I thought a company of that size was reliable??

Hope you have more luck...

---

### Post by dinodeman on 2009-05-08
> 
Hope you have more luck... 

I had a bit more luck then you. I send my laptop to the store where I bought the EEE PC and they helped me getting a new SSD drive and now it's working again. I found another issue with this EEE 900. It seems that the battery discharges very fast even when it's not turned on. I saw on a TV program that this problem was a known problem. I have decided not to take action, because I don't want to loose the machine again for 4 weeks.

---

### Post by Joraeim on 2010-01-30
I am having the exact same problem. Same error messages and everything.
I also tried mkfs. It is saying block 0 is bad.

root@ubuntu:/home/ubuntu# mkfs -t ext4 -c /dev/sda1
mke2fs 1.41.9 (22-Aug-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
246016 inodes, 983973 blocks
49198 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1010827264
31 block groups
32768 blocks per group, 32768 fragments per group
7936 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736

Checking for bad blocks (read-only test): done                                
Block 0 in primary superblock/group descriptor area bad.
Blocks 0 through 2 must be good in order to build a filesystem.
Aborting....

---

### Post by dinodeman on 2010-01-31
> I am having the exact same problem. Same error messages and everything. I also tried mkfs. It is saying block 0 is bad.

Did you try to restore the superblock with one of the backup superblocks? If that didn't work then your drive is probably messed up. Try "sudo e2fsck -b 32768 /dev/sda1" to restore the superblock.

---

### Post by j-ro on 2010-02-21
> **Joraeim said:**
> I am having the exact same problem. Same error messages and everything.
I also tried mkfs. It is saying block 0 is bad.

root@ubuntu:/home/ubuntu# mkfs -t ext4 -c /dev/sda1
mke2fs 1.41.9 (22-Aug-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
246016 inodes, 983973 blocks
49198 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1010827264
31 block groups
32768 blocks per group, 32768 fragments per group
7936 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736

Checking for bad blocks (read-only test): done                                
Block 0 in primary superblock/group descriptor area bad.
Blocks 0 through 2 must be good in order to build a filesystem.
Aborting....
i've the very same problem: although mine started after i logged in to a new openbox session (said i had a badly formed xml file for rc.xml --- can't see how this matters).  since i couldn't do anything and there was no data worth saving, i tried to reinstall.  from that point on, everything described above is identical.  

i spent a lot of time looking for answers, but it seems like the answer is that there is no (good) answer.  hopefully, someone can tell me i'm wrong!

---

### Post by j-ro on 2010-02-21
> **j-ro said:**
> i've the very same problem: although mine started after i logged in to a new openbox session (said i had a badly formed xml file for rc.xml --- can't see how this matters).  since i couldn't do anything and there was no data worth saving, i tried to reinstall.  from that point on, everything described above is identical.  

i spent a lot of time looking for answers, but it seems like the answer is that there is no (good) answer.  hopefully, someone can tell me i'm wrong!

a quick addendum: i just checked the usb install 'cd' from the install menu, it said there were 97 errors!  but this is not true on my other computers.  the md5 checksum, uhh, checked out fine too.

---

