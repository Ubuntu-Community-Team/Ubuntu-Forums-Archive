---
title: "Need some simple :D raid advice / guidance Handholding may be required :)"
date: 2011-05-13
forum: Hardware
---

### Post by skaramanger on 2011-05-13
Greetings,

I've spent the better part of this evening reading posts from my fellow Ubuntu enthusiasts regarding their raid woes.  Most of these posts have to do with running Ubuntu on a raid setup.

I don't want to do that.  I have a sata 2 250GB drive and I installed two 1GB Samsung Sata Spinpoint's. I turned on 'fakeraid' in bios and set them up to be mirrored (I know I have heard that software raid is better), but I just wanna do it this way (for now :)).
 
I'm running ubuntu 10.10 Maverick.

```
$ uname -r 2.6.35-28-generic
```

```
$ sudo dmraid -s
[sudo] password for : 
*** Set
name   : nvidia_hjcabcaf
size   : 1953525120
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
```

```
$ dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs
```

```
$ sudo blkid 
/dev/sda: TYPE="nvidia_raid_member" 
/dev/sdb1: LABEL="root" UUID="0eaa02f9-8d4a-40b6-b282-9001ca383700" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: LABEL="Home" UUID="b34aa478-7495-4e4a-bfba-f31d24d268eb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="e3c944e6-00af-44f5-b937-6d5999325148" TYPE="swap" 
/dev/sdb7: LABEL="Downloads" UUID="969e7370-b0e5-4127-85e1-745cb500d6b8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc: TYPE="nvidia_raid_member" 
/dev/sdd5: LABEL="My_Book" UUID="0a3b8fc4-062f-4ff6-81d5-f3ba03f1d425" SEC_TYPE="ext2" TYPE="ext3" 
```


From what I can gleen from the output, is that I don't have much more to do except configure it. Here is where some handholding might come in:).  I looked at the Fakeraid howto:

[HTML]https://help.ubuntu.com/community/FakeRaidHowto?highlight=%28raid%29[/HTML]

and that didn't enlighten me as to just setting it up.  So I look at the man page:

```
man dmraid
```

It provided some help, and more questions. For instance,

I have 2 1GB drives in a mirror 1, What would be a nice default activation/setup look like?  What would the command line look like? Block sizes?  Swap partition size? I will be storing video and music files and miscellaneous documents.  If you have read this far thank you. If you can provide me some feedback even greater kudos to you.

Tia,
Skaramanger

---

### Post by skaramanger on 2011-05-14
How's about a bump?

---

### Post by skaramanger on 2011-05-14
Ok,

I tried using gparted to install dos partition table on the raid 1 array and that fragged the meta data for the raid.  So I made sure that the meta data was deleted:

```
dmraid -e /dev/mapper/nvidia_raidname
```

I then rebooted and reinitialized the raid.  Now using part of the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto"):

```
#mkfs.ext4 /dev/mapper/nvidia_aabeeafj
```

This created a ext4 filesystem on the array using the whole space.  I did this w/o creating a partition table as explained in the above mentioned howto.  I am bothered by this.  It shouldn't work this way should it?  If my assumption is correct, then what type of partion table should be created on the array? Dos? Another?  After the partition table is created, I should then be able to use gparted to add partitions using different filesystems. Right?

Tia.

---

### Post by skaramanger on 2011-05-15
> **skaramanger said:**
> Ok,

I tried using gparted to install dos partition table on the raid 1 array and that fragged the meta data for the raid.  So I made sure that the meta data was deleted:

```
dmraid -e /dev/mapper/nvidia_raidname
```

I then rebooted and reinitialized the raid.  Now using part of the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto"):

```
#mkfs.ext4 /dev/mapper/nvidia_aabeeafj
```

This created a ext4 filesystem on the array using the whole space.  I did this w/o creating a partition table as explained in the above mentioned howto.  I am bothered by this.  It shouldn't work this way should it?  If my assumption is correct, then what type of partion table should be 
created on the array? Dos? Another? After the partition table is created, I should then be able to use gparted to add partitions using different filesystems. Right?

Tia.

Ok,  I realize in my thick head yes, you must create a partition table before you create filesystems. I knew that!(Just avoid doing anything when your tired :>). Alas though, must the partition table be dos and of course (if that's the case) one of the partitions has to be bootable (not what I want) before it will write partition table.  Also, I was using cfdisk to create the partiton table. I noticed that there is a selection of partition type of FD which is a type of software raid disk.  How might this selection apply or not?

Thanks again,

I'll be posting back my activity

skaramanger

---

### Post by skaramanger on 2011-06-21
Ok,

Been up and running for awhile now using software raid 1.

---

