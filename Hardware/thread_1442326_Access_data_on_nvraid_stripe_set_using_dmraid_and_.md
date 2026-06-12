---
title: "Access data on nvraid stripe set using dmraid and loop devices?"
date: 2010-03-29
forum: Hardware
---

### Post by tyn on 2010-03-29
Hi,
I am in one of those terrible situations...  My motherboard died and I am left with a nvidia nforce raid stripe set that I need to get data off.  I guess I should have setup that backup regime.  Some search results have suggested that dmraid may be my white knight.

I have pulled the data off each of the disks (3 of them) into image files (using ddrescue) and created loop devices (/dev/loop[1-3], using losetup).  I am running 32bit ubuntu 9.10 btw.

When I do a "dmraid -ay" it tells me it found a raid set but has not activated it. When I do a "dmraid -r" it tells me I have a raid5 array on one of my /dev/sd? devices.  dmraid seems to be ignoring my loop devices altogether. 

Does anyone know if dmraid actually works with loop devices?  If it does is there a way for me to point it directly at the devices and get it to do its auto-magic?

Is there a simpler/better way of doing this?


Thanks

---

### Post by tyn on 2010-04-01
Hi,
No one seems to know anything about dmraid and loop devices.  I posted on this forum, Nvidia's forum and linuxquestions.  Finally I tried to subscribe to the redhat's mailing list for dmraid and never got a response - I suppose the list is dead.

In desperation I pulled apart one of my other PC's and physically connected the nvraid stripe set to the motherboard.  I created an X-Ubuntu 9.10 live-USB stick and booted up with my fingers crossed.  The system started and dmraid auto-detected the stripe array.  For those who may be interested:
- use the sudo dmraid -ay to force auto-detection of arrays and activate them
- use the sudo dmraid -r command to get details on the arrays
- you can also use gparted to see the raid devices and their respective partitions; just like any other drive
- I created a directory to use as a mount point for my partition
- look in /dev/mapper for the names of your partitions
- I used sudo mount -t nfts -o users,owner,ro,umask=000 dev/mapper/<partiton name> <mount dir> to mount the partition

This successfully mounted by stripe set partition.  Then I tar'd the contents to a USB drive using sudo tar -zcvf /media/<USB drive>/files.tar.gz <mount dir>  To get the files out of the tar archives I use tar -zxvf  /media/<USB drive>/files.tar.gz and the files extract into the directory you are running the tar command from.

I wish I could have found an answer for using loop devices; but, alas, it was not to be.  It certainly would be a huge improvement if dmraid were updated to support loop devices.

---

