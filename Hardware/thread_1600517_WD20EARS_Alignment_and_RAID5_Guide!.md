---
title: "WD20EARS Alignment and RAID5 Guide!"
date: 2010-10-19
forum: Hardware
---

### Post by megamandos on 2010-10-19
Like many other people, I bought WD20EARS drive for an array and thought I would just toss them into my server and set up an array and would be done by sun down. And like many people, I was dead wrong. What was supposed to be a one-night deal turned into a month long battle with RMA's (newegg is pretty fast) and filed SATA cards, bad drives, bad cables, and bad SATA controllers on my old motherboard. So after all this crap, I still had to deal with figuring out how to align partitions on a WD20EARS with a GPT partition table (since the drives have 4KB sectors), and kept finding guides that said to use 0 or 1 or 64 for the sectors to start your partitions with. Well I tried those, and got ridiculously low speeds for syncing the array. 

So I read somewhere that Windows 7 knew how to align them properly, so i popped one into my windows 7 box and created a partition on it. It started at sector 2048! (1MB into the disk). So i make an ext4 partition in its place with the same start and ending sectors, and then struggled with that a bit and it kept locking up as the sync got to about 93.2% and then two of the drives would fail out of the array and another would be turned into a spare. 

After a week of trying different methods of this i tried setting pins 7 and 8 on the drives, well that failed too, the box wouldn't even boot. I read somewhere that it messed with the controller. So i gave up on that for a few days until i decided to do the same thing but put the disk into my win7 box, and the windows 7 worked fine, i made a new GPT table and did the same with the rest of the disks. I noticed it still didnt get very good read/write performance. I decided to go ahead and try and align the partitions manually even with the 7+8 pins jumped.

Suffice it to say that after some serious trial and error I cam up with a configuration that worked. I have pin 7+8 jumpered on all 4 drives, I created and formatted XFS partitions starting at sector 2048 and ending on sector 3907029134 on each drive. I then "forced" a raid5 creation. And I am currently waiting for that to finish, but am getting GREAT sync speeds, of around 70-90MB/s.

So here are the steps:

[LIST=1]
[*]Physical preparation: Ensure pints 7+8 are jumpered (if you don't have jumpers you can buy them are most computer stores or online)

[*]Download and install the necessary software.
```
sudo apt-get install xfsprogs
```

[*]Change user to root.
```
sudo -s
```

[*]Create the partitions on EACH drive (replace sda with whatever drive you are doing).
```
parted /dev/sda
mklabel gpt
yes
unit s
mkpart

xfs
2048
3907029134
quit
```

[*]Format the partitions. Do the following for each drive. (again, replace sda with whatever drive you are doing)
```
mkfs.xfs /dev/sda1
```

[*]Create the array with the following command (change the number of drives as required and be sure that the devices are correct):
```
mdadm --create /dev/md0 --chunk=2048 --force --level=5 --raid-devices=4 /dev/sdb1 /dev/sdd1 /dev/sdc1 /dev/sde1
```

[*]Create your /etc/mdadm/mdadm.conf file, without this it will fail to recognize the array after you reboot! Execute the following commands:
```
sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

[*]Wait for the array to finish syncing. You can reboot while it is going, but [COLOR="Red"]DO NOT CONTINUE WITH THIS GUIDE (OR ATTEMPT TO PARTITION /dev/md0)UNTIL IT IS COMPLETELY SYNC'D!![/COLOR] You can expect this to take 8-12 hours! You are able to watch the status of it via:
```
watch -n 0.2 cat /proc/mdstat
```
or
```
watch -n 2 mdadm --detail /dev/md0
```

[*]Format the new array.
```
mkfs.xfs /dev/md0
```

[*]Add the array to your fstab (File System TABle). You can use gedit, or your favorite command line editor. Add the following line to the end of your "/etc/fstab" file.
```
/dev/md0 /media/raidarray auto defaults 0 3
```
You can change "/media/raidarray" to wherever you want it to mount on boot.

[*]Mount the new raid array:
```
mount --all
```
[/LIST]

Now you should have a raid5 array mounted at /media/raidarray or where ever you put it.

---

### Post by srs5694 on 2010-10-19
> **megamandos said:**
> Suffice it to say that after some serious trial and error I cam up with a configuration that worked. I have pin 7+8 jumpered on all 4 drives, I created and formatted XFS partitions starting at sector 2048 and ending on sector 3907029134 on each drive. I then "forced" a raid5 creation. And I am currently waiting for that to finish, but am getting GREAT sync speeds, of around 70-90MB/s.

This story is rather surprising. Jumpering those pins causes the drive to offset its sector numbers by 1, so that what the computer believes is 63 is actually 64 (and others changed in a similar way). In theory, you should get better performance with that jumper *not* set. Certainly every test I've seen (and I actually [ran a set of tests myself](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)) suggests that, in a single-drive configuration, performance can take a significant hit when partitions are misaligned.

I would speculate that your syncing operation is doing reads of large blocks of data at once, so you're not seeing the performance problems of this configuration; but when you start using the disk, the performance won't be as great as it should be, particularly if you write a lot of small files. In my tests, XFS took 1.8 times as long to write small files on improperly aligned partitions. Whatever you do, don't use ReiserFS, ext2fs, or JFS on that drive! (See Figure 2 in the article to which I linked.)

Of course, I realize you tried doing it the "right" way and had difficulties. I suspect you've got two or three interacting problems, with the Advanced Format alignment issues being just one of them (and the one that's not a show-stopper).

---

### Post by megamandos on 2010-10-20
I am still having issues, seems to be alignment of the partition on the md0 device. And i am still having trouble with my motherboard so i ordered a new motherboard and bought some new RAM. Overnight, they should be here in a couple days.

---

### Post by srs5694 on 2010-10-20
> **megamandos said:**
> I am still having issues, seems to be alignment of the partition on the md0 device. And i am still having trouble with my motherboard so i ordered a new motherboard and bought some new RAM. Overnight, they should be here in a couple days.

In that case, I recommend you try again *without* using the jumper and with 2048-sector (1 MiB) alignment on your next attempt.

---

### Post by megamandos on 2010-10-21
View the attachment, it happened when i was formatting on of the drives. Granted, it was mounted over USB, an I/O error is bad either way.

The second try worked though.

---

### Post by megamandos on 2010-10-21
Ok so, without the jumper installed, sync speeds are around 11MB/s when forced.

They are all XFS with partitions starting at sector 2048.

Also i got this error twice: "md: could not bd_claim sde1"

```
        Version : 1.2
  Creation Time : Thu Oct 21 22:41:59 2010
     Raid Level : raid5
     Array Size : 5860529472 (5589.04 GiB 6001.18 GB)
  Used Dev Size : 1953509824 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Thu Oct 21 22:41:59 2010
          State : clean, resyncing
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           Name : big-server:0  (local to host big-server)
           UUID : eb6e693e:436cee15:1c63f80d:9a9422c8
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
       2       8       33        2      active sync   /dev/sdc1
       3       8       65        3      active sync   /dev/sde1

```

Each of the drives look just like this, no jumper is installed.
```
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdc: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name  Flags
 1      2048s  3907024064s  3907022017s  xfs

```

After a little while speeds improved, but not by much.

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[3] sdc1[2] sdd1[1] sdb1[0]
      5860529472 blocks super 1.2 level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  1.1% (22409472/1953509824) finish=1541.6min speed=20876K/sec
      
unused devices: <none>

```

---

### Post by psusi on 2010-10-22
The purpose of the jumper is to allow Windows XP to perform normally with a start sector of 63.  Current versions of partitioning tools on Ubuntu will start the partition at sector 2048, like vista and windows 7, in which case you do NOT want the jumper.  You can use gpt if you want to, but you do not have to since the drive is not larger than the 2tb limit of the msdos partitoin table.  The fact that it uses 4kb sectors internally ( and lies and claims it is 512 bytes still ) has no bearing on anything other than the optimal alignment.  Which filesystem you use is also immaterial.

---

### Post by megamandos on 2010-10-22
Second attempt with the EXACT same configuration:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[3] sdc1[2] sdd1[1] sdb1[0]
      5860536960 blocks super 1.2 level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  0.0% (227712/1953512320) finish=28925.3min speed=1125K/sec
      
unused devices: <none>

```

This time the error i see is slightly different, only by the disk:
```
[2844.077019] md: could not bd_claim sdd1
```

---

### Post by megamandos on 2010-10-22
> **psusi said:**
> The purpose of the jumper is to allow Windows XP to perform normally with a start sector of 63.  Current versions of partitioning tools on Ubuntu will start the partition at sector 2048, like vista and windows 7, in which case you do NOT want the jumper.  You can use gpt if you want to, but you do not have to since the drive is not larger than the 2tb limit of the msdos partitoin table.  The fact that it uses 4kb sectors internally ( and lies and claims it is 512 bytes still ) has no bearing on anything other than the optimal alignment.  Which filesystem you use is also immaterial.

So any guess as to the major performance degradation?

> Current versions of partitioning tools on Ubuntu will start the partition at sector 2048...

Thats not correct. Gparted starts at sector 34 by the way.

---

### Post by psusi on 2010-10-22
> **megamandos said:**
> So any guess as to the major performance degradation?


Are you sure that you have the jumper OFF?  And you will need to reformat when changing the position of the jumper.

> **megamandos said:**
> 
Thats not correct. Gparted starts at sector 34 by the way.

Which version are you using?  The one that ships with 10.04 should start at sector 2048 just like Windows Vista and 7.

---

### Post by megamandos on 2010-10-22
> **psusi said:**
> Are you sure that you have the jumper OFF?  And you will need to reformat when changing the position of the jumper.

I think i know what a jumper looks like... also,you don't only have to reformat it, you have to make a new partition table.

> **psusi said:**
> Which version are you using?  The one that ships with 10.04 should start at sector 2048 just like Windows Vista and 7.

I am running Ubuntu Server 10.04 x64 Long Term Support version. I appreciate the idiot checks.

---

### Post by psusi on 2010-10-22
Well, I can only say that it works for me.  As of lucid parted starts at sector 2048, and I get fine performance with my WD10EARS.  You might try running hdparm -t on the drive itself, and then on the partition and compare the results.  With no jumper, and the partition starting on sector 2048, the results should be the same.

I wonder if parted didn't default to sector 2048 because you had it use gpt?  You might try with msdos instead.

---

### Post by srs5694 on 2010-10-22
A few comments and suggestions:


[list]
[*]Sector 34 is the first available sector in a default GPT setup, so psusi's idea that GParted might be using 34 with GPT and 2048 with MBR is plausible. It should be possible to force it to 2048 (or some lesser multiple-of-8 sector value) with any partitioning system. As a general rule, libparted-based tools seem to require more knowledge and effort to get this to work than do the fdisk family or GPT fdisk; however, the libparted-based tools have been improving rapidly. I can't check whatever Ubuntu 10.04 uses, since I don't have a 10.04 installation at the moment.
[*]*If* the speed problems are related to the Advanced Format alignment issues (and I don't think that should be assumed), the use of hdparm to test speed on the disk as a whole vs. on a partition is unlikely to produce any useful results. This is because hdparm does a large read operation; but the alignment issues have almost no effect on read performance. The biggest effects are seen on write operations involving small files, because it's those operations that require modifying many inodes and other low-level filesystem data structures that are likely to straddle the 4096-byte physical sector boundaries, thus necessitating extra operations.
[*]In theory, improper alignment should only cause speed problems, as psusi states. Theory and practice often don't quite agree, however; there could be bugs in filesystem (or RAID) code that get triggered only when disk performance is inconsistent, for instance; or there could be a bug in the disk's firmware code that gets triggered only under conditions that are rare except when doing certain filesystem or RAID operations.
[*]Megamandos, are your latest tests (from posts #5 and later) using the new motherboard and memory you said you were getting in post #3? If not, you might want to wait until you get those components, since it could be the problem lies with them.
[*]It's conceivable, and perhaps even likely, that the problem is due to a bad hardware interaction, and might not even be related to the Advanced Format system specifically. Certainly this wouldn't be the first time that Component X doesn't get along with Component A, even though Component X works with Component B and Component Y works with Component A.
[*]It might be worth just returning the WD drives and buying another brand. Certainly it's not worth spending hours trying to debug something that's behaving in the flaky manner you describe, at least not if you think the problem may be related to bad or incompatible hardware.
[/list]

---

### Post by megamandos on 2010-10-23
> **srs5694 said:**
> A few comments and suggestions:


[list]
[*]Sector 34 is the first available sector in a default GPT setup, so psusi's idea that GParted might be using 34 with GPT and 2048 with MBR is plausible. It should be possible to force it to 2048 (or some lesser multiple-of-8 sector value) with any partitioning system. As a general rule, libparted-based tools seem to require more knowledge and effort to get this to work than do the fdisk family or GPT fdisk; however, the libparted-based tools have been improving rapidly. I can't check whatever Ubuntu 10.04 uses, since I don't have a 10.04 installation at the moment.
[*]*If* the speed problems are related to the Advanced Format alignment issues (and I don't think that should be assumed), the use of hdparm to test speed on the disk as a whole vs. on a partition is unlikely to produce any useful results. This is because hdparm does a large read operation; but the alignment issues have almost no effect on read performance. The biggest effects are seen on write operations involving small files, because it's those operations that require modifying many inodes and other low-level filesystem data structures that are likely to straddle the 4096-byte physical sector boundaries, thus necessitating extra operations.
[*]In theory, improper alignment should only cause speed problems, as psusi states. Theory and practice often don't quite agree, however; there could be bugs in filesystem (or RAID) code that get triggered only when disk performance is inconsistent, for instance; or there could be a bug in the disk's firmware code that gets triggered only under conditions that are rare except when doing certain filesystem or RAID operations.
[*]Megamandos, are your latest tests (from posts #5 and later) using the new motherboard and memory you said you were getting in post #3? If not, you might want to wait until you get those components, since it could be the problem lies with them.
[*]It's conceivable, and perhaps even likely, that the problem is due to a bad hardware interaction, and might not even be related to the Advanced Format system specifically. Certainly this wouldn't be the first time that Component X doesn't get along with Component A, even though Component X works with Component B and Component Y works with Component A.
[*]It might be worth just returning the WD drives and buying another brand. Certainly it's not worth spending hours trying to debug something that's behaving in the flaky manner you describe, at least not if you think the problem may be related to bad or incompatible hardware.
[/list]

All very good information. I am going to try a few more tests. I overnighted the new motherboard, and it actually did stop some errors and other minor issues i was having. BTW everything i have stated since i said i was getting a new motherboard has been with the new one. As far as i know, it had compatibility problems before, but they are gone now. So i am going to run a few more tests and if i cannot get the performance i require then i will return the drive for a different brand. I have trusted in WD for a long time, and would hate to have to admit that they have failed me.

---

### Post by megamandos on 2010-10-23
What kind of sync speeds should i be expecting with a properly aligned raid5 4-disk array.

I am getting 32Mbps with a raid5 right now... its got 4 wd20ears in it

---

### Post by psusi on 2010-10-23
> **megamandos said:**
> What kind of sync speeds should i be expecting with a properly aligned raid5 4-disk array.

I am getting 32Mbps with a raid5 right now... its got 4 wd20ears in it

I'd say at least 100 MB/s ( not Mbps ).

---

### Post by megamandos on 2010-10-23
Yeah, sorry meant MB/s, mbps is easier to type lol. And btw, iostat is saying im getting ~200MB/s on those drives while it is syncing, and cat /proc/mdstat is saying 40MB/s... This whole time I have never seen mdstat say over 90MB/s, no matter what I have tried.

---

### Post by megamandos on 2010-10-23
Ummm... Well i was going through my syslog and found this:

```
Oct 23 09:54:37 big-server kernel: [ 3229.431840] ata4.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x0
Oct 23 09:54:37 big-server kernel: [ 3229.432475] ata4.00: irq_stat 0x40000008
Oct 23 09:54:37 big-server kernel: [ 3229.432796] ata4.00: failed command: READ FPDMA QUEUED
Oct 23 09:54:37 big-server kernel: [ 3229.433116] ata4.00: cmd 60/00:10:ff:a9:db/01:00:0b:00:00/40 tag 2 ncq 131072 in
Oct 23 09:54:37 big-server kernel: [ 3229.433117]          res 41/40:00:97:aa:db/00:00:0b:00:00/40 Emask 0x409 (media error) <F>
Oct 23 09:54:37 big-server kernel: [ 3229.433805] ata4.00: status: { DRDY ERR }
Oct 23 09:54:37 big-server kernel: [ 3229.434169] ata4.00: error: { UNC }
Oct 23 09:54:37 big-server kernel: [ 3229.439731] ata4.00: configured for UDMA/133
Oct 23 09:54:37 big-server kernel: [ 3229.439748] ata4: EH complete
```

the most interesting line is just before the bottom:
```
Oct 23 09:54:37 big-server kernel: [ 3229.439731] ata4.00: configured for UDMA/133
```

isnt UDMA/133 the old speed for PATA drives?? And why is it changing to UDMA 133?

---

### Post by psusi on 2010-10-23
Sounds like you have a bad drive.  Open the disk utility and look at the SMART values.  Run the long self test.

---

### Post by megamandos on 2010-10-23
K. I'm running the long test on all 4 drives. It says they should be done by tomorrow around 3pm central time. How can I tell which drive is "ata4.00"?

---

### Post by psusi on 2010-10-23
Look for the drive that the disk utility says is on port 4.

---

### Post by megamandos on 2010-10-24
Searched through the kernel log and saw that all of the WD20EARS drives were being set to UDMA/133 max on startup. I don't know why.

---

### Post by megamandos on 2010-10-24
I removed the jumpers, this time before i created a partition table I did a R/W benchmark on all 4 drives. The results are ****. Take a look.

---

### Post by megamandos on 2010-10-24
> **megamandos said:**
> Ummm... Well i was going through my syslog and found this:

```
Oct 23 09:54:37 big-server kernel: [ 3229.431840] ata4.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x0
Oct 23 09:54:37 big-server kernel: [ 3229.432475] ata4.00: irq_stat 0x40000008
Oct 23 09:54:37 big-server kernel: [ 3229.432796] ata4.00: failed command: READ FPDMA QUEUED
Oct 23 09:54:37 big-server kernel: [ 3229.433116] ata4.00: cmd 60/00:10:ff:a9:db/01:00:0b:00:00/40 tag 2 ncq 131072 in
Oct 23 09:54:37 big-server kernel: [ 3229.433117]          res 41/40:00:97:aa:db/00:00:0b:00:00/40 Emask 0x409 (media error) <F>
Oct 23 09:54:37 big-server kernel: [ 3229.433805] ata4.00: status: { DRDY ERR }
Oct 23 09:54:37 big-server kernel: [ 3229.434169] ata4.00: error: { UNC }
Oct 23 09:54:37 big-server kernel: [ 3229.439731] ata4.00: configured for UDMA/133
Oct 23 09:54:37 big-server kernel: [ 3229.439748] ata4: EH complete
```

the most interesting line is just before the bottom:
```
Oct 23 09:54:37 big-server kernel: [ 3229.439731] ata4.00: configured for UDMA/133
```

isnt UDMA/133 the old speed for PATA drives?? And why is it changing to UDMA 133?

Turns out that this was a bug in the ACPI code. 

Still trying to figure out what is with the poor performance.

Made a post on the WD forums here: [http://community.wdc.com/t5/Desktop/WD20EARS-horrible-performance-whether-aligned-or-not-4-of-them/td-p/71182](http://community.wdc.com/t5/Desktop/WD20EARS-horrible-performance-whether-aligned-or-not-4-of-them/td-p/71182)

---

### Post by psusi on 2010-10-24
You are still not paying attention to this:

> Oct 23 09:54:37 big-server kernel: [ 3229.433117]          res 41/40:00:97:aa:db/00:00:0b:00:00/40 Emask 0x409 **(media error)** <F>

You have some bad sectors.  Look at the smart numbers and run a long self test.

---

### Post by megamandos on 2010-10-26
> **psusi said:**
> You are still not paying attention to this:



You have some bad sectors.  Look at the smart numbers and run a long self test.

Actually the test completed, and there are no bad sectors. But it says one the drives that they have a read error rate of 1500/s? idk what this means, but one of the drives failed to complete SMART, and said "READ ERROR", as in it couldn't read SMART values. I thought it might be a bad cable so i tried it again, this time no error, but the cable doesn't "seem" bad. Then, again, i don't have x-ray vision. I am considering asking SD to replace them with 2TB WD20EADS drives, as i have two of those and they run fine.

---

### Post by psusi on 2010-10-26
You need to look at the relocated, pending, and uncorrectable counters.

---

### Post by megamandos on 2010-10-30
> **psusi said:**
> You need to look at the relocated, pending, and uncorrectable counters.

I think i am going to ask WD to replace these with WD20EADS.

---

### Post by esetnik on 2010-12-17
> **megamandos said:**
> Turns out that this was a bug in the ACPI code. 

Still trying to figure out what is with the poor performance.

Made a post on the WD forums here: [http://community.wdc.com/t5/Desktop/WD20EARS-horrible-performance-whether-aligned-or-not-4-of-them/td-p/71182](http://community.wdc.com/t5/Desktop/WD20EARS-horrible-performance-whether-aligned-or-not-4-of-them/td-p/71182)

I have the same errors as you appearing in my console when I watch messages with tail -f /var/log/messages

I am running ubuntu 10.10 desktop on a fresh install and I get the ata errors on all 4 disks under heavy disk access.  I followed your install and noticed the errors first during raid resyncing.  Now the disks are continually being dropped off the RAID.  Did you end up getting rid of the WD20EARS? I don't know what to do with them to get a functioning raid 5 setup.  And to the people who say its a drive failure, I have 4xWD20EARS all displaying the same error messages and I recently plugged in a 5th sata drive (an old WD model 500gb drive) and did not have any of these errors.

---

### Post by psusi on 2010-12-17
If you are seeing media errors then the drives are bad.  Check the SMART numbers in the disk utility and RMA them.

---

### Post by esetnik on 2010-12-22
There is no way I got 4 bad drives.  I ordered 2 from newegg and 2 from amazon.  I can't rma them because i've already had them for too long.  I did smart on each and they all came back fine.

---

### Post by psusi on 2010-12-22
Did you run the long selftest?  It takes like 12 hours.  Also the drives have a 3 year warranty iirc, so yes, you can RMA them if they are bad.  Also there are a lot of people over on the wdc forums complaining about these drives failing early, even in batches.  I got one over the summer and it seemed fine, then the  next morning was dead as a doornail.  The replacement is still working well though.

---

### Post by Wazz72 on 2010-12-22
I'm having problems using 4 WD10EARS building a raid 5 array.  
the array has built fine, but I'm having problems partitioning it.
I end up with around 2.7tb of usable space. I know because of the disk alignment I have to start on sector 64, and start the following partitions +8 from the previous ones.
Is it better to have 4 smaller partitions or 1 larger one?  Also what it the best type of partition table to use GPT?  I did have it as MSDOS originally but had problems on the last partition.   Which is the best method of formatting the partitions?  and do I use EXT2 or EXT3?  
Why don't my partitions appear in the Ubuntu Disk Utility, it just shows the volume and the 1st partition.

Any help would be appreciated.

Thanks
Warren.

---

### Post by psusi on 2010-12-23
Use ext4 for the fs.  As for partitions, it depends on if you are talking about partitioning the drives, or the array.  The msdos partition table is limited to 2tb, so if you are partitioning the array, it is larger than that so you must use gpt.  If you are partitioning the disks, then you can stick to msdos.  I would suggest you use msdos to partition the disks into two raid partitions, one small, and the rest of the space to the other.  Then turn the small partitions on each disk into a raid array to use for swap, and the large partitions into a raid array to use for /.

---

### Post by Tiftof on 2011-01-06
At first I create an Ext2 partition on my wd20ears using ubuntu disk utility and started copying from another drive (sata to sata). This gave me a speed of around 20MB/s. This seemed slow and I reformatted using the instructions of the first post (starting an ext2 partition at sector [noparse]2048[/noparse]). This boosted the copying speed to 50-80MB/s!

Thanks for the tip!

---

### Post by srs5694 on 2011-01-06
> **Tiftof said:**
> At first I create an Ext2 partition on my wd20ears using ubuntu disk utility and started copying from another drive (sata to sata). This gave me a speed of around 20MB/s. This seemed slow and I reformatted using the instructions of the first post (starting an ext2 partition at sector 2048). This boosted the copying speed to 50-80MB/s!

Was that a typo or corruption by an overzealous formatting by the forum software? It looks like you wrote sector 204, but the first post to which you refer specifies 2048. 204 is not divisible by 8, so it's not optimal for Advanced Format drives. It's conceivable it'd be better than sector 63, but in theory it shouldn't be as good as sector 2048 (or 64 or any other number that's divisible by [noparse]8).[/noparse]

If the forum software goofed, you can go in and edit your post, placing a [noparse][noparse][/noparse] tag before the number and a [/noparse] tag after it, so that the forum software won't change the number inappropriately, as it sometimes does.

Edit: Yup; it's the forum software bug. It got me at the end of my first paragraph, too. I've fixed it in my post now....

---

### Post by megamandos on 2011-01-15
All the drives were bad that I had. Apparently there are some major design flaws with the WD**EARS line of drives that causes manufacturing likely to cause issues with drive stability. I no longer am a fan of Western Digital.

EDIT: I found out it was a problem with the linux driver "ata_generic". I blacklisted the driver and now i get around 105MBps sync speeds. Alignment is still an issue, however. The performance change is huge. I am running 10.10 on the server with the RAID5 array in it. Turns out that driver has caused slow HDD performance in older versions of ubuntu as well.

---

### Post by kelargo on 2011-03-03
I was looking at getting four of these drives for my server and setting up software raid 5.  

After RMA'ing the drives, are they holding up now? 

I always thought WD was better than the other drive makers.. idk any more.

---

### Post by rich1842 on 2011-04-23
This page may be useful to anyone having problems with WD Advanced Format disk drives:

[http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system](http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system)

---

### Post by srs5694 on 2011-04-23
> **rich1842 said:**
> This page may be useful to anyone having problems with WD Advanced Format disk drives:

[http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system]("http://wdc.custhelp.com/app/answers/detail/a_id/5655/%7E/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system")

That's certainly better than what they used to say, which was that Linux would use such drives with proper alignment by default! My main gripe with that page as it is now is that it puts a lot of emphasis on kernel versions, which really isn't very relevant. AFAIK, the Linux kernel has never really been a stumbling block; it's the partitioning tools that need to support such drives. In an ideal world, the kernel should be able to properly identify the drives, but contrary to what that page says, I have yet to see evidence that it can. I've got two such drives myself, and I've tested several different kernel versions. The system calls that are supposed to return the true physical sector size have always told me that my Advanced Format drives have 512-byte physical sectors, which they don't.

---

### Post by psusi on 2011-04-25
> **srs5694 said:**
> The system calls that are supposed to return the true physical sector size have always told me that my Advanced Format drives have 512-byte physical sectors, which they don't.

That is because the drives themselves lie and report a 512 byte sector size.  I complained to WD support about this when I got mine last year and they don't seem to give a crap.

---

### Post by srs5694 on 2011-04-25
> **psusi said:**
> That is because the drives themselves lie and report a 512 byte sector size.  I complained to WD support about this when I got mine last year and they don't seem to give a crap.

True, but my point is that the WD page being discussed emphasizes kernel support for Advanced Format drives as being important. Since their own drives lie about their physical sector size, the kernel is not an important support factor.

---

### Post by psusi on 2011-04-25
> **srs5694 said:**
> True, but my point is that the WD page being discussed emphasizes kernel support for Advanced Format drives as being important. Since their own drives lie about their physical sector size, the kernel is not an important support factor.

Very true.  I'll have to check later tonight if they have a firmware update that may fix the issue as I have heard reports that newer drives are no longer lieing, so maybe they have fixed that issue, and then you do need a kernel that can read it correctly.

---

### Post by srs5694 on 2011-04-25
I bought a 320 GB 2.5-inch WD drive for a Mac Mini in January, and it doesn't report things correctly. Then again, it might not have been all that recent a model, although I bought it fairly recently.

Even if a new drive does report its sector sizes correctly, I don't think you *need* a kernel that can interpret that information. Having such a kernel might help *if* your partitioning software uses the relevant kernel calls. I know for a fact that my own GPT fdisk (gdisk and sgdisk) doesn't do so -- I don't want to write the code and release it if I can't test it, lest there be a bug that could make matters worse! I haven't checked fdisk and libparted recently, but when I checked last (half a year or a year ago), they didn't do the checks; although both reported both physical and logical sector sizes, the code at that time just printed the same value twice. Maybe one or both tools now does the right thing, but unless or until you hear confirmation of this, or verify it in the source code, I strongly recommend you do *not* assume that they do just because they report it.

---

### Post by psusi on 2011-04-26
> **srs5694 said:**
> I bought a 320 GB 2.5-inch WD drive for a Mac Mini in January, and it doesn't report things correctly. Then again, it might not have been all that recent a model, although I bought it fairly recently.

AFAIK, they don't make a 320 gb drive using 4kb sectors.  It is only the 1TB+ green series that is using 4kb sectors.

> **srs5694 said:**
> I haven't checked fdisk and libparted recently, but when I checked last (half a year or a year ago), they didn't do the checks; although both reported both physical and logical sector sizes, the code at that time just printed the same value twice. Maybe one or both tools now does the right thing, but unless or until you hear confirmation of this, or verify it in the source code, I strongly recommend you do *not* assume that they do just because they report it.

Parted has been able to use the values for about a year now iirc, but defaults to a 1 MB alignment if the kernel does not know what optimal alignment should be used ( if /sys/block/sdX/queue/optimal_io_size is zero ).

---

### Post by srs5694 on 2011-04-26
> **psusi said:**
> AFAIK, they don't make a 320 gb drive using 4kb sectors.  It is only the 1TB+ green series that is using 4kb sectors.

It's a 2.5-inch WD Scorpio Blue, WD3200 BPVT. The drive has a label on it saying that it uses Advanced Format technology. (I don't recall the exact wording, but it was pretty obvious.) The spec sheets (available [here]("http://www.wdc.com/wdproducts/library/?id=217&type=8")) also mention Advanced Format technology for drives in the "PVT" series. That's a little ambiguous, since mine is a "BPVT" model, but given the label on the drive, I figure it's an Advanced Format drive.

WD introduced the Advanced Format technology with its 1 TB and larger "green" drives, as you say, but that was over a year ago (December of 2009, IIRC). They announced at the time that they'd be using the technology in other drive lines in the future, and that's clearly been happening. I don't know what percentage of WD drives are currently Advanced Format.

FWIW, I've heard of Advanced Format drives from other manufacturers, too. One was one of the smaller manufacturers (Samsung or Fujitsu, I think); but I've heard of Seagate drives that use the technology, too.

At this point, I'd say it's best to assume that any new drive uses Advanced Format. That assumption will be wrong in many cases, but given the [consequences of misalignment,]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/") such an assumption is prudent. (Aligning partitions on a non-Advanced Format drive as for an Advanced Format drive has only the most trivial negative consequence -- the loss of between 512 bytes and a bit under 1 MiB of storage space, depending on the details.)

---

### Post by psusi on 2011-04-26
I guess time is catching up with me.  Does this drive also report 512 bytes for both physical and logical size in hdparm -I?

I would have hoped that they would start conforming to the standard which WD is usually good at.

---

### Post by srs5694 on 2011-04-26
> **psusi said:**
> I guess time is catching up with me.  Does this drive also report 512 bytes for both physical and logical size in hdparm -I?

Yup. I even compiled the latest kernel just to be sure my earlier tests didn't fail because of an outdated kernel (I'd been running the stock Ubuntu 10.10 kernel, 2.6.35-22-generic):

```

$ **uname -a**
Linux tunesmith 2.6.38.4 #1 SMP Tue Apr 26 21:24:49 EDT 2011 i686 GNU/Linux

$ **cat /proc/scsi/scsi**
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: MATSHITA Model: CD-RW  CW-8124   Rev: DACH
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD3200BPVT-0 Rev: 01.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05

$ **sudo parted /dev/sda print | grep size**
Sector size (logical/physical): 512B/512B

$ **sudo hdparm -I /dev/sda | grep Physical **
    Logical/Physical Sector size:           512 bytes

$ **cat /sys/block/sda/queue/optimal_io_size **
0

```

---

### Post by tuomi on 2011-08-15
Any updates on this issue, Im currently sitting on 4 of these trying to get em to play with mdadm, allthough one keeps dropping out. Have to be sure that its faulty before I RMA it though..

But with this abrupt end of this thread I get to wonder, is there a good solution for this problem out there?

---

### Post by syn4pse on 2011-08-18
Hello,
having the same issue here trying to setup a raid 5 with 5 of those drives. I had some help from a linux guru and just created my raid.

sync speeds don`t look that bad:

```

Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdf1[4] sde1[3] sdd1[2] sdc1[1] sdb1[0]
      7814045696 blocks super 1.2 level 5, 2048k chunk, algorithm 2 [5/5] [UUUUU]
      [>....................]  resync =  2.4% (47024920/1953511424) finish=324.4min speed=97930K/sec
      
unused devices: <none>

```

I also performed a quick read check ( while the raid is still resyncing )

I ll let you know how it played out for me...

---

### Post by syn4pse on 2011-08-19
so, raid finished syncing. so i quickly threw a mkfs.ext4 towards that /dev/md0 and after that was done i copied a file over and got like 25MB/s which is from my point of view a verry crappy performance. I was expecting a way better outcome due to the high sync speeds. Anybody has found/created a good working configuration yet?

---

### Post by DennisF on 2013-01-02
Hey all,

Thanks to everybody posting in this thread, it was mighty helpful in getting to the bottom of correctly getting a WD20EARS raid 5 up. I wanted a bit more on top of what was described here (LVM and performance checks for starters) and that required a bit more fiddling. I've [written a small howto ]("http://dennisfleurbaaij.blogspot.nl/2013/01/setting-up-linux-mdadm-raid-array-with.html")on getting the raid array running and adding LVM while keeping an eye on performance.

Cheers,
Dennis

---

