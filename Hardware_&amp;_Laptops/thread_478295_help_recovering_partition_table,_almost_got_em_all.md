---
title: "help recovering partition table, almost got em all"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by __knk__ on 2007-06-19
hey all, im an ex-ubuntu user using debian(sid/unstable) now but considering the much larger community and the similarities between debian and ubuntu i thought id post it here.  just thought id clarrify that i hav nothing against ubuntu and its contributed to debian alot.

my problem is that for one reason or another(pretty sure its not my fault:)) my partition tables been completely erased. havnt tried to boot the system or nething of course in order to (hopefully) get my stuff back. its a 320gb seagate sata for those who are interested.  ive also only been mounting in read only.

so to start off, ive got:
1st partition for macos
2nd for windows
3rd for debian
extended starting at 4th
home drives 5th
1gb swap 6th
and 7th(one i need to recover) is ext3 and has most of my music etc.  

only hav an oldish backup left on my xbox stupid me backed up mostly everything onto the other 250 gb hdd EXCEPT the music and a few other things.

so ive got going with a knoppix livecd using gpart and fdisk ive managed to get to know the location of the macos partition windows debian home drives.  however the swap and 7th one(my stuff) will not mount.

i was thinking if there were any logs available on the debian partition which would hav a log of fdisk because i remember it was run in the last session since the problems occured.  

could someone please give me a hand with this, really cant seem to figure this one out on my own.:).

btw if i do get it mounted do you guys know of any livecds with the ntfs-3g driver installd if not ill get around to installing to a memory stick

edit:  found this in /var/log/installer on the debian partition.  but dont kno what the values are in?, possibly blocks:s. im not too good with this kinda stuff. just needa be able to add them with fdisk but that reads in sectors i think?


parted_server: OUT: 1	32256-21474868735	21474836480	primary	hfs+	/dev/scsi/host1/bus0/target0/lun0/part1	

parted_server: OUT: 2	21476206080-42952412159	21476206080	primary	ntfs	/dev/scsi/host1/bus0/target0/lun0/part2	

parted_server: OUT: 3	42952412160-72950008319	29997596160	primary	ext3	/dev/scsi/host1/bus0/target0/lun0/part3	

parted_server: OUT: 5	72950040576-92953889279	20003848704	logical	ext3	/dev/scsi/host1/bus0/target0/lun0/part5	

parted_server: OUT: 6	92953921536-93957373439	1003451904	logical	linux-swap	/dev/scsi/host1/bus0/target0/lun0/part6	

parted_server: OUT: 7	93957405696-320070320639	226112914944	logical	ext3	/dev/scsi/host1/bus0/target0/lun0/part7	


could someone please gimme some help, thanks :)
edit2:ok pretty sure its in bytes...any way to get a more accurate reading because dividing by 512 isnt exactly the most accurate method lol

---

### Post by Sloddy Shipper on 2007-06-19
Take a look at this -

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

I just came across this while answering another post about lost partitions and trying to repair my own unbootable windows partition, I've not tried it yet but it looks promising. Hopefully it can help you too.

---

### Post by __knk__ on 2007-06-19
thanks a heap man that did the trick....gpart didnt come newer near as close as testdisk did.  gpart seemd to have problems with the extended partitions.  and i was only two sectors off the bloody numbers i needed lol, not bad for manual work:).  thx again buddy

---

