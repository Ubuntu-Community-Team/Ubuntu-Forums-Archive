---
title: "Ubuntu 5.10 installer not detecting partitions"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by nexus76 on 2006-02-07
Hi all, 

I'm currently trying to install Ubuntu 5.10 on a dual boot machine (currently XP and Mepis Linux - the latter of which I want to overwrite) but when the installer comes to the partitioning phase it identifies my 60Gb drive as free space only - whereas XP confirms there are 5 partitions (1 NTFS, 2 FAT and 2 "unknown" that are used by mepis). I've not come across this problem when installing previous versions of Ubuntu before so am a bit lost about how I can get past this point - any advice greatfully received (if you need more info - just ask)

Cheers

nexus

---

### Post by lha on 2006-02-07
People with this kind of problems have usually had something strange with partitions. If you send output of 'fdisk -l' I'd take a look on your partition table.

---

### Post by nexus76 on 2006-02-07
Ok here is the - painstakingly rewritten:) - output from fdisk (using mepis) 

Disk /dev/hda = 60GB    60022480896 bytes
16 heads, 63 sectors/track, 116301 cylinders
Units = cylinders of 1000 * 512 = 516096 bytes

Device        Boot    Start        End        Blocks        ID    System
/dev/hda1   *         1            20321     10241406    7     HPF/NTFS
/dev/hda2              20322     48223     14062608    83    Linux
/dev/hda3              48394     116301    34225632    f     W95 Ext'd (LBA)
/dev/hda4              49386     78449     14648224     c    W95 FAT32(LBA)
/dev/hda5              48394     49385     499905       82    Linux Swap
/dev/hda6              78450     116301   19077376+    c    W95 FAT32(LBA)

Partitions 1,2,3 & 4 are reported to not end on cylinder boundaries.

nexus

---

### Post by lha on 2006-02-07
[QUOTE=nexus76]Ok here is the - painstakingly rewritten:) - output from fdisk (using mepis) 

Disk /dev/hda = 60GB    60022480896 bytes
16 heads, 63 sectors/track, 116301 cylinders
Units = cylinders of 1000 * 512 = 516096 bytes

Device        Boot    Start        End        Blocks        ID    System
/dev/hda1   *         1            20321     10241406    7     HPF/NTFS
/dev/hda2              20322     48223     14062608    83    Linux
/dev/hda3              48394     116301    34225632    f     W95 Ext'd (LBA)
/dev/hda4              49386     78449     14648224     c    W95 FAT32(LBA)
/dev/hda5              48394     49385     499905       82    Linux Swap
/dev/hda6              78450     116301   19077376+    c    W95 FAT32(LBA)

Partitions 1,2,3 & 4 are reported to not end on cylinder boundaries.

nexus[/QUOTE]

Your extended partition has two logical partitions, hda5 and hda6. Between them you have hda4 what seems like a primary partition! This is not good. Logical partitions should be next to each other, not spread around the drive. I've seen few of these cases get fixed after deleting partitions that are causing grief. A good place to start would be that swap partition, but I can't guarantee it's enough... :( Did you use Disk Druid to make those partitions?

---

### Post by nexus76 on 2006-02-07
[QUOTE=lha]Your extended partition has two logical partitions, hda5 and hda6. Between them you have hda4 what seems like a primary partition! This is not good. Logical partitions should be next to each other, not spread around the drive. I've seen few of these cases get fixed after deleting partitions that are causing grief. A good place to start would be that swap partition, but I can't guarantee it's enough... :( Did you use Disk Druid to make those partitions?[/QUOTE]

Disk Druid? - No....if my memory is correct the only partitions I've created were done through the XP and Ubuntu install procedures....I dont think I did any explicit partitioning when installing Mepis Linux.....I'm not particulary experienced with partitioning and since XP is curently my primary OS I'd probably be using PartitionMagic...I could afford to get rid of both swap and linux partitions but the others I'd really like to keep the data on....can you foresee any problems I might encounter?

nexus

---

### Post by lha on 2006-02-07
[QUOTE=nexus76]Disk Druid? - No....if my memory is correct the only partitions I've created were done through the XP and Ubuntu install procedures....I dont think I did any explicit partitioning when installing Mepis Linux.....I'm not particulary experienced with partitioning and since XP is curently my primary OS I'd probably be using PartitionMagic...I could afford to get rid of both swap and linux partitions but the others I'd really like to keep the data on....can you foresee any problems I might encounter?

nexus[/QUOTE]

Well, there's not much I can see besides problems...

Deleting hda2 won't be useful here, as it isn't one of those problematic partitions. Is there any way you could back up your data? Maybe if you copied data from hda4 into hda2, delete hda4, shrink hda3 to minimum size possible without touching hda5 and hda6, and finally create a new primary partition in the free space, you could make it work. This isn't the only options and there may be an easier solution. Remember to make backups if you try this, fiddling with partitions can result in disaster. Also, be sure to have a backup plan.

PS. I'm not a Partition Magic fan. It has caused me some troubles but if it suits you... The most important this with partitions is to be sure you are doing things to the right partition, so a familiar program is a good thing.

---

### Post by nexus76 on 2006-02-07
[QUOTE=lha]Well, there's not much I can see besides problems...

Deleting hda2 won't be useful here, as it isn't one of those problematic partitions. Is there any way you could back up your data? Maybe if you copied data from hda4 into hda2, delete hda4, shrink hda3 to minimum size possible without touching hda5 and hda6, and finally create a new primary partition in the free space, you could make it work. This isn't the only options and there may be an easier solution. Remember to make backups if you try this, fiddling with partitions can result in disaster. Also, be sure to have a backup plan.

PS. I'm not a Partition Magic fan. It has caused me some troubles but if it suits you... The most important this with partitions is to be sure you are doing things to the right partition, so a familiar program is a good thing.[/QUOTE]

lol <long sigh> This is all quite ironic - both my OS's have been working fine for a year like this!! I was only thinking of installing Ubuntu to give a family member a taste of it to see if it suited them - I'm not opposed "in principle" to a total format of the drive - I had to do that this time last year - and that time the data I had *was *crucial - backing up the majority of the data probably isnt viable for me and most if it is "i want" data not "i need" data - music collection etc.....:-k ....most of the stuff I could get hold of again online - but thats a whole different story :P

---

### Post by lha on 2006-02-08
[QUOTE=nexus76]lol <long sigh> This is all quite ironic - both my OS's have been working fine for a year like this!! I was only thinking of installing Ubuntu to give a family member a taste of it to see if it suited them - I'm not opposed "in principle" to a total format of the drive - I had to do that this time last year - and that time the data I had *was *crucial - backing up the majority of the data probably isnt viable for me and most if it is "i want" data not "i need" data - music collection etc.....:-k ....most of the stuff I could get hold of again online - but thats a whole different story :P[/QUOTE]

I do understand this is a bit surprising issue, but some partitioners just aren't that picky on partition tables and as it seems, allow users to create faulty partition tables.

On my previous system I had some strange this going on in my partition table. I had two overlapping partitions, one partition changed its partition type to Amoeba when I  booted my main os and logical partitions weren't in correct order. (Luckily those partitions that were overlapping were testing partitions, so I didn't lose any valuable data.) When I wanted to repartition my drive before installing Ubuntu, cfdisk (my favourite partitioner) refused to work with that drive, even though my main system had worked fine for 1 ½ years. I ended up deleting a lot of partitions before I got cfdisk to cooperate.

Maybe you could install Ubuntu without using the installer. [Debootstrapping from a Knoppix cd]("https://wiki.ubuntu.com/Installation/FromKnoppix") seems more complicated than regular install, but it might let you install Ubuntu without repartitioning. If Mepis has coped with your drive as it is, Ubuntu can probably do the same... Hopefully.

---

