---
title: "Mdadm array lost on Thunderbolt 3 drive"
date: 2021-01-23
forum: Hardware
---

### Post by John Jason Jordan on 2021-01-23
I have a Thunderbolt 3 enclosure that has two full length PCI cards, each of which holds two 7.68TB U.2 NVMe drives. I set up the four drives as one 31TB RAID0 array with mdadm about a month ago, and it was all working beautifully until yesterday. The enclosure has always been connected to the Thunderbolt 3 port on a Lenovo dock, which is then connected to the Thunderbolt 3 port and power port on my Thinkpad P73. The array was mounted using its UUID with a line in /etc/fstab. 

(Note: Please hold the comments about how bad RAID0 is; this array is backed up nightly to a NAS mirror, so RAID1 would be pointless. And all the files are still there on the NAS, so if my array is hopelessly gone I can recreate it and copy everything back from the NAS.)

In /dev the four drives appear, but the mdm file (the array) is not there, although I dimly remember seeing it there before. Worse, the four drives appear, but every few minutes they disappear and then reappear a few seconds later. Something weird is going on, and whatever it is may be why my array went away. But, while the drives disappear and reappear in /dev, the dock also connects to ethernet and several USB drives, all of which function without pauses. Before I recreate the array I want to be sure that it is truly gone, and more importantly, I want to know what happened, so hopefully I can make sure I don't have a repeat. 

I need some clues.

---

### Post by TheFu on 2021-01-26
Just saying that you have a RAID0 and it is backed up nightly would have been sufficient for me. You'd be surprised at how many people think all RAID modes have protection .... and that backups are necessary than RAID.  Backups are 1000x more important than RAID-anything, so you've nailed that.

Can't say that I understand the physical connections - but if the separate devices are showing up, fine. I don't need to.

Whenever I create a RAID array, I
[LIST=1]
[*]keep a copy of the creation commands; those few commands can be very helpful later.
[*]create notes about the purpose and why non-standard settings may have been used - like if I change the stripe sizing due to performance testing done before. For example, my stripes are either 128K or 256K based on the actual hardware I'm using and the size of files it holds.  For a long time, everyone used 64K stripes, but that was much slower on my hardware.
[*]make notes for the commands to re-assemble the array, should anything bad happen. That would be a loose connector or a failed drive. Those notes are made when everything about mdadm is fresh, so I'm not hunting down the commands 3 yrs later at 4am. I just don't do enough array work to keep everything fresh in my mind.
[*]always create a partition on each disk to be used for the array. Never use the full disk. This is mainly because 3 yrs later the exact disk model may not be available and every storage device is just a little different in the number of sectors provided. It will also be helpful when you've pull a disk for archival, but don't properly label it. Most partitioning tools would see storage with RAID data on it as garbage and may offer to format it. That would be bad. With a partition, I know exactly the correct size in sectors needed and regardless of the actual storage used, I can force the needed size for replacement storage. I learned this the hard way. Bought a replacement HDD only to find it was short a few sectors.  I've also grabbed a disk that didn't have a partition and it looked like garbage. Fortunately, before I formatted it, I recalled something about RAID and didn't.
[/LIST]

**Gather some facts first**
[LIST]
[*]What do the log files show related to these storage devices and the array?
[*]What are the current devices used. The /dev/ and UUIDs would be good.  For lurkers, the device names like /dev/sdj can and do change so don't use those.
[*]What is the current state of the array.  **/proc/mdstat** and **mdadm --detail /dev/mdXYZ** can provide that.  
[*]In theory, the partitions used to create the array should be in **/etc/mdadm/mdadm.conf **Show that.  
[/LIST]
Those 4 things should get us started.

---

### Post by John Jason Jordan on 2021-01-26
@TheFu,
Thanks for the reply! While waiting I kept poking and eventually decided that I'd better just bite the bullet and try to recreate the array, and then copy everything back to it from the NAS. I started at about  5pm Monday; it is now 10am Tuesday and rsync has finished about 75% of the 10TB on the NAS. My ethernet is supposedly gigabit, but everything has to get from the NAS to my laptop, then out the TB3 port on the laptop to the enclosure holding the drives. I'd be surprised if I really get half of what things are rated for.

Creating the array took about ten hours of work. Part of the problem was that, like you, I create an array, it works, and I forget about how I created it, so years later I have to look everything up again. This time I did as you suggested - a simple text file containing all the commands and error messages and how to fix them. And believe me, the error messages were massive. Weird things, like I created the array as /dev/md0, and after rebooting it was md127. WTH? And I used Gparted to create a partition and format it, but formatting failed over and over with 30 or 40 incomprehensible error messages. And once I finally succeeded in formatting it without errors I copied the UUID from Gparted and tried to use it to mount the partition, but got 'no such device.' So I put the UUID and the rest of the mount command into /etc/fstab, and then did 'sudo mount -a' - and then it worked. Except that then I couldn't copy files to it because it was owned by root, even though I had 'user' in fstab. There are days when I want to throw this computer into the river and go do something useful with my life.

The worst part is that I still have no idea why the drives kept disappearing and reappearing in /dev, nor do I have a clue about what happened to cause my original array to go away. I have other arrays that have lasted for many years, but this was my first one with U.2 drives in a Thunderbolt 3 enclosure.

---

### Post by TheFu on 2021-01-26
The slowest part of the storage chain will be the limiting factor.  I have 25-40 Gbps here between some systems, but that doesn't matter when the source and destination are on a 7200 rpm spinning HDD.  The HDD write performance will always be the limiting factor.  When going through as many jumps as your storage does, any limitations for each controller along the way will likely be where the slow down comes, regardless of the storage write performance.

BEFORE you create the array, did you make partitions on each disk?  Not sure from reading above that happened.  mdadm arrays are built from partitions.  Then they get either a volume manager or a file system.

[LIST]
[*]disk
[*]partition
[*]mdadm array
[*]file system / volume management then a file systems under the VM stuff.
[/LIST]
That's the hierarchy.

Disappearing devices are usually caused by a loose cable.  All my disk array connections have screw-in connectors. Never just a USB connection.  

I've been burned by USB-like connectors too many times. Never again.  The little vibrations seem to be the problem. Over time, that makes for a loose connection.

---

### Post by John Jason Jordan on 2021-02-01
The array was working fine, and I copied all the files to it from the NAS backup. It took roughly 24 hours to copy all 10TB, but the time that it took doesn't really matter.

I should add that I read elsewhere that mdadm does not need partitions; you can just use the drive as listed in /dev. That is how I created it, and eventually it worked without errors. Also, the appearing/disappearing of the drives cannot be a loose connection, unless all four drives have a loose connection in the same way. And the enclosure has no on-off switch; it turns itself on and off when the TB3 cable is inserted/removed. And it is noisy; if the cable was disconnected it would be obvious.

This morning I tried to open a torrent file (for the ISO for a distro) in Ktorrent, only to have Ktorrent refuse to add the torrent because the location to save it to (the array) was read-only. WTH? I've been reading and writing to/from that array ever since I created it, including files that I wrote to it last night. I use either Thunar or PCManFM for a GUI file manager, which displayed all the files on the array as always. But when I right-clicked on a file the Rename and Delete options were missing. I took this as confirmation that overnight the array had suddenly become read-only. I have no clue how this could be.

Normally this array (/dev/md127) gets mounted at boot from a line in /etc/fstab: 'UUID=09ed8807-e45a-4dac-8f4b-5ad9a07be90a /media/jjj/Data auto nosuid,nodev,nofail,x-gvfs-show,user 0 0.' So I decided to umount it and then mount it again with 'sudo mount -a.' The umount command resulted in 'can't read superblock on /dev/md127p1,' although apparently it did umount it. And when I then tried to mount it again I got the same error, and the mount failed. And curiously, of the four drives (nvme1n1, nvme2n1, nvme3n1, nvme4n1), in /dev only nvme4n1 shows a partition (nvme4n1p1). I just figured that this had something to do with some weirdness of mdadm - the command to create the array listed the four drives in order, so nvme4n1 was the last one, and apparently that's where mdadm decided to add the partition. But what do I know?

It looks like I am going to have to nuke the array and start all over again from the start. This does not happify me.

---

### Post by John Jason Jordan on 2021-02-01
What I said about the drives and the partition in /dev was from how I remembered things after creating the array. Just now I looked at /dev, and things are very different, in weird ways. Here is the current list:

md127
md127p1

nvme1n2
nvme2n2
nvme3n2
nvme4
nvme4n1
nvme4n1p1
nvme4n1p2
nvme5
nvme6
nvme7
nvme8

OK, this is just bizarre. The last four, nvme5-8, don't exist. Since there are four of them, I am guessing that they are an echo of the four drives in the array, but why? It makes no sense.

And originally all four drives were listed as nvme1 and nvme1n1 (and ditto for the other three drives). And now the namespace has become 2 for the first three drives. Why? There was no 'p1' for the array; it had just one entry 'md127.' And now nvme4 has two partitions. Where did nvme4n1p2 come from?

Edit: I rebooted, and the array is now read-write. But the list of devices in /dev is still weird - it remains exactly as above. And when I launched Ktorrent it couldn't find the files for half of the torrents, all of which are on the array.

---

