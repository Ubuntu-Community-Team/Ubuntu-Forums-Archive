---
title: "[SOLVED] what to do (i did) to fix a disk mis partitioned by gparted shrink (resize)"
date: 2008-11-04
forum: General Help
---

### Post by lakitu on 2008-11-04
hey all. i am only beginning, but i just had a dealing with ubuntu/linux that seemed to cost me a partition, but in fact was recoverable. note that my partition was an ntfs; i haven't tested this with ext2/ext3/reiser etc.

cause: gparted shrink ("resize") partition function

symptom: trying to mount volume gives error, inspecting it in gparted says "file system is damaged" or something to that effect (sorry, didn't write it down). it is not any message otherwise, it is something to the effect that the file system is damaged.

solution: use Testdisk: 
1. get it, by enabling The Universe repository (go to System . Administration . Software Sources, & tick "Community Maintained Opensource (Universe)"), & then install it (either thru searching "testdisk" at Synaptic package manager (go to System . Administration . Synaptic package manager . search "testdisk"), or alternatively just go to a terminal & enter ```
sudo apt-get install testdisk
```. 
2. read & follow [Herman's TestDisk HowTo]("http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_a_Lost_Partition_With_"), because that has a full screenshot-&-all walkthru. 

what i did was do a lot of reading, & make no hasty decisions. if you're missing a partition, or have other serious harddisk errors, one of the biggest mistakes you can make is write to the disk, either unintentionally (e.g. automounting it) or intentionally (trying something that you're not sure on). ask here or in #ubuntu in IRC freenode (chat). i am not an expert, but i am just posting this because i fixed what was frighteningly broken, on my comp, & wanted to help others who do the same.

lakitu

---

