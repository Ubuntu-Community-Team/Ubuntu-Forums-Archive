---
title: "Dumb  &quot;re&quot;-formatting question"
date: 2005-01-10
forum: Installation &amp; Upgrades
---

### Post by brtp on 2005-01-10
Total newbie so expect off the wall :confused:    I have 80g hard drive and I  installed warty on the whole disk,  used reisers, not sure why,  the  question ,  is there anyway to shrink the partition size and then allow dual boat  without reinstall ??  :oops:   I have it all set up nicely thanx to all the howtos and  any help on this would be greatly appreciated,,  i386 arch,,,   thnx in advance

---

### Post by swerner on 2005-01-10
First you need back up all your important data.

To shrink an reiserfs partition it first needs to be unmounted, this could be problem if your system is all on one partition. If you have the Ubuntu Live CD, boot using the Live CD and run the following (as root),
```
umount  /dev/hda1
resize_reiserfs  -s  40000M  /dev/hda1
```where /dev/hda1 is the partition you wish to resize to 40000 MB (40 Gig). 

Now check the partition has been resized
```
mount /dev/hda1
df  --block-size  1048576
```the last line will give you the size of each partition in MB.

resize_reiserfs does not actually resize your partition, you have to the program cfdisk which is a semi-user-friendly disk partitioning tool. 
```
cfdisk /dev/hda
```Delete the hda1 partition and create a new primary partition, at least 40000 MB. Change the partition type to 83. Then create the next partition. Remember to choose the "write" option before you exit. Now reboot your computer. MAKE SURE YOU DON'T MAKE THE PARTITION SMALLER THAN WHAT YOU SPECIFIED USING RESIZE_REISERFS!!!! It's safest to make the new partition just slightly larger than what you specified, by a few MB (say 2-5).

---

### Post by brtp on 2005-01-11
thanx so much for the help,,, sorry  :sad:  I took so long to repost,   ,,  everything worked  wonderful til reboot,  then  kernal panic,,, so,,, :-& ,,,   what else,,, but to,    :oops: ,   redo everything,,   but the good news is I learned  bunches, stacks, and thank you oh so much for the hellp,,, BTW,  the boot problem was --- trying to read reiser**,   and the format was  other,  anyway thanx again,  now all set up and working like a charm---

---

