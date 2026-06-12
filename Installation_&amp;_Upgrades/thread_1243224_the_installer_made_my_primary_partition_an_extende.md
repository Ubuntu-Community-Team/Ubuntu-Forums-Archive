---
title: "the installer made my primary partition an extended one.."
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by aarons6 on 2009-08-18
im trying to figure out how to fix this, but somehow i ran into a slight problem.

here is what happend.

i used the live cd, and it chose to resize my windows vista ntfs partiton and put 2.5gb of free space at the end.

everything went fine and it loaded into kubuntu.

i then went back to load into vista and it wouldnt boot.

i checked out online and i figured out how to fix it, but vista is having issues.
it seems my sda1 partition got turned into an extended one. (the one vista was loaded on)
then kubuntu made the logical drive that vista is now on sda5 and sda2 is where it installed itself.

so my map looks like this
sda1 extended
  sda5 NTFS 
  sda6 SWAP
sda2 EXT3

trying to install vista wont work because it complains about not finding a drive to install too.. this is because you can only install vista on a primary partition.

the problem im having is this drive has about 100gb of files on it.. files i dont want to redownload (mostly movies) i cant backup because of the size.

i know for a fact the primary partiton, the only partition on the drive was sda1 before it got resized.. and i installed vista on it about 20 minutes before i installed kubuntu.

ok so i know have downloaded a live gparted cd.

ive checked some and i found this.
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt

if i tell the computer that sda5 is sda1 and hose the extended partition ill keep my files and make vista happy?? 

this is all i want. 

sda1 NTFS
sda2 SWAP
sda3 EXT3

ive deleted the swap part, and the ext part.. so now my map looks like this.
sda1 extended
sda2 empty
sda3 empty
sda4 empty
sda5 NTFS

running sfdisk now, gives me a warning.. 
it says extended partition does not start at a cylinder boundary.. 
I don't know how to fix that.

any ideas?
i know i can just delete everything and start over, but id rather not.

---

### Post by aarons6 on 2009-08-18
going to reply to my own post..

i did this.
sfidsk -d /dev/sda > part.txt
i then edited the part.txt moving sda5 to sda1
and ran
sfdisk --force /dev/sda < part.txt

and it worked..

my drive looks like this
sda1 NTFS 
unallocated 
 

woot :)

now i wonder why the installer made my drive all extended in the first place.

---

### Post by dandnsmith on 2009-08-18
> **aarons6 said:**
> 
now i wonder why the installer made my drive all extended in the first place.

I don't believe it did - sda5 and sda6 would be within the extended filesystem space, while sda2,sda3 will be primary partitions.

What did the partition table show for start/end info before you corrected it?

---

### Post by aarons6 on 2009-08-18
what i started with was
sda1 extended whole drive minus 2.5gb 
sda5 NTFS logical whole extended drive minus 300 some mb
sda6 SWAP 300some mb
sda2 EXT3 2.5 gb



i qiuckly found out also that 2.5gb is not even close to enough heh..

i just chose the side by side method.

i really should have just made space with the windows vista partitioner.. first..

---

