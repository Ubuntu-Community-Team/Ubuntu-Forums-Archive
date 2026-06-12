---
title: "HDD format and partition help"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by flightcrank on 2005-09-25
im getting all sorts of weird reults using mkfs and programs like gparted.

i have a ide hard disk named /dev/hdd. i would like to format it and and one partition  using ext3

so how do i format it, then partition it.

better yet, can a use the ubuntu install cd's menu to do this, as that way i know it will work.

---

### Post by greenstar on 2005-09-25
yes you can use the install cd, but if you're not actually installing ubuntu that would be the long way to do it.

I'd also recommend using reiserfs rather than ext3. As I understand it, ext3 was designed so that ext2 users could migrate to a journalling filesystem, rather than designed from the ground up to be a solid journalling file system as was reiserfs.

greenstar

---

### Post by flightcrank on 2005-09-25
[QUOTE=greenstar]yes you can use the install cd, but if you're not actually installing ubuntu that would be the long way to do it.

I'd also recommend using reiserfs rather than ext3. As I understand it, ext3 was designed so that ext2 users could migrate to a journalling filesystem, rather than designed from the ground up to be a solid journalling file system as was reiserfs.

greenstar[/QUOTE]
 ok but this is to host big files. i herd reiserfs is fast for small files. in any evnet i dont care what file system.

what are the commands used to format a hard drive under ubuntu. then the commands to make one huge partition of the 80gig drive i have.

---

### Post by flightcrank on 2005-09-25
i figured it out, first you set up partitions.

i wanted one big one to span the whole drive.

sudo fdisk /dev/hdd

then press "d" to delete any partition that were there.

press "n" for new partition and create a extened partition so span the whole drive.

then press "n" again to create the actual logical partition, again to span the whole drive.

then press "w" to save and write partition to hard drive.

/dev/hdd1 = extended, /dev/hdd5 = logical (the actual file system)

then type 

sudo mkfs -t ext3 /dev/hdd5

this will format the logical partiton for in the ext3 file system format.

it may take a short while to finish

then mount it, in my case, i made a directory /media/ide2

and then typed

sudo mount /dev/hdd5 /media/ide2 -t ext3

and done, i can now use the drive. becasue its permanant HDD its best to edit /etc/fstab. to load the drive on startup

---

### Post by andrewsawyer on 2005-09-26
Hey everyone,

I'm having the same problem :-(

I have followed the instructions in the post above, and formatted /dev/hdb.

When typing fdisk -l, I get the following (I'm only giving the info for that particular drive)

```

Disk /dev/hdb: 300.0GB, 300001443840 bytes
240 heads, 63 sectors/track, 38752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

Device Boot   Start       End      Blocks         Id   System
/dev/hdb1        1      39572    292965088+        5   Extended

```

after this it then goes onto the next drive.

Typing 'sudo mkfs -t ext3 /dev/hdb5' gives the error:
```

The device apparently does not exist; did you specify it correctly?
```
Checking in the Flie Browser shows the following:
hda
hda1
hda2
hda5
hda6
hdb
hdb1
hdc
hdc1
hdc2
hdc5

hda has my ubuntu installation on one partition, a swap partition and a /home partition.  hdb is obviously blank, and hdc is currently NTFS however my plan is to *fix* hdb, copy all the info from hdc and then wipe out and reformat hdc.

I would really appreciate if someone could let me know the command to create the new partition on hdb so that I can mount it.  Filesystem wise, I was using ext3 as that was used in the example above.  The drive is going to be pretty much filled with 300-700 Mb files.  Would ReiserFS be better or no?  I've heard XFS is prone to dying and I would like something reletively stable.  While I back up the important files (family pics etc) it's very difficult to back up a total of 900Gb of data - as I'm sure you can imagine.

Your help would be much appreciated.

---

### Post by flightcrank on 2005-09-26
you for got to do this step

then press "n" **again** to create the actual **logical** partition, again to span the whole drive.

you have already made the extended part now you have to make the actual partition that you will format the filesystem onto. read the parts in bold.

typing fdisk -l says you have no hdb5, you have to make it first with fdisk

---

### Post by andrewsawyer on 2005-09-26
Doh!  That easy hey!

Thank you.  And thank you for the quick reply!

Andy

---

