---
title: "Lacie disk mini 500GB XFS drive recovery"
date: 2009-03-26
forum: Hardware
---

### Post by MuShoe on 2009-03-26
Hello,

I have a Lacie edMini 500GB NAS drive that stopped resonding a week or so ago.  I have pulled the drive out (yes, I know it voids warranty) and plugged it directly into my computer.  To keep things simple, I disconnected the 2 SATA drives that I usually use in that computer, put only the faulty drive in and booted from the Ubuntu 8.04 live cd.

The BIOS detects the drive at a Segate 500GB drive (which it is), but when I run 'sudo fdisk -l', I get nothing back.  the GUI partition table tool also shows no drives connected.  However, when I go to /dev, I see sda, sda1, sda2, sda5, sda6, sda7, sda8, and sda9.  I know from other internet searching that Lacie puts 7 XFS partitions on theis NAS drives, so something is telling linux that there are 7 partitions there.

When I try to mount any of those drives using
```

sudo mount -t ext3 /dev/sda1 /mnt/lacie

```
I am told that the device does not exist.  The same thing happens with sda2-9.

I tried running the xfs_repair utility as listed below:
```

xfs_repair /dev/sda1

```
and got the error that the primary superblock could not be found and the recovery attempt just stops.  The same happens when I try it on sda2-9.

I tried running dmesg by the following command:
```

dmesg | grep sda

```
and I got some I/O block errors, but I can't recall off the top of my head exactly what they were (I'm not at my home PC right now, so I can't check...).

I do have a backup that is a few months old and the only thing that I *really* need off of this drive are some recent pictures that my daughter downloaded to it.

Any help would be most appreciated.

Thanks!

Jeff

---

### Post by MuShoe on 2009-04-01
bump

---

### Post by jimmylymm on 2009-05-24
Sorry not a direct reply to your problem, but hopefully an answer to anyone with Lacie edmini 500GB gigabit problems.
My drive stopped responding this morning.  Blue light comes on, but disk doesn't properly spin up. Not visible on network, no access via usb either.
So either its a dodgy power pack, or the mainboard has gone.
 
Took the drive out of the enclosure and plugged into a PC via sata cables. The partitions were visible, but under windows they were useless.
So I downloaded ubuntu, burnt the iso image to a cd. booted the PC from cdrom
Fired up ubuntu (without altering my pc)
Went to 'places' on the menu.
Low and behold, all the partitions were visible as folders. As my USB disk drive was also visible I just copied all the files from one area to the other.
So data all recovered. :D
I can now figure out what to do about my NAS server. new powerpack or bin
Hope this helps someone.:D

---

### Post by karrika on 2009-06-06
> **MuShoe said:**
> Hello,

I have a Lacie edMini 500GB NAS drive that stopped resonding a week or so ago.  I have pulled the drive out (yes, I know it voids warranty) and plugged it directly into my computer.  To keep things simple, I disconnected the 2 SATA drives that I usually use in that computer, put only the faulty drive in and booted from the Ubuntu 8.04 live cd.

The BIOS detects the drive at a Segate 500GB drive (which it is), but when I run 'sudo fdisk -l', I get nothing back.  the GUI partition table tool also shows no drives connected.  However, when I go to /dev, I see sda, sda1, sda2, sda5, sda6, sda7, sda8, and sda9.  I know from other internet searching that Lacie puts 7 XFS partitions on theis NAS drives, so something is telling linux that there are 7 partitions there.

When I try to mount any of those drives using
```

sudo mount -t ext3 /dev/sda1 /mnt/lacie

```I am told that the device does not exist.  The same thing happens with sda2-9.

I tried running the xfs_repair utility as listed below:
```

xfs_repair /dev/sda1

```and got the error that the primary superblock could not be found and the recovery attempt just stops.  The same happens when I try it on sda2-9.

I tried running dmesg by the following command:
```

dmesg | grep sda

```and I got some I/O block errors, but I can't recall off the top of my head exactly what they were (I'm not at my home PC right now, so I can't check...).

I do have a backup that is a few months old and the only thing that I *really* need off of this drive are some recent pictures that my daughter downloaded to it.

Any help would be most appreciated.

Thanks!

Jeff

My LaCie Ethernet Big Disk 1T NAS developed a flaw and lost all files. I decided to open up the enclosure and found two 500G disks. The partitions are not XFS directly. I found out that on the first disk the partition sda2 and on the second disk the whole sdb disk creates a linear md disk.

First I downloaded the Ubuntu livecd iso-image 9.04. From my Ubuntu desktop I chose to make a bootable USB stick from System->Administrator->USB Startup Disk Creator.
I used a 4G USB stick and reserved 1G of memory for read/write.

Then I got a new 500G USB disk and formatted that for ext3 to allow it to use big files. My backup is going to have tar archives that are hundreds of gigabytes in one file.

To rescue the data I removed both drives from the LaCie enclosure and put them in a normal PC. The first disk was marked by an orange paper label.
 
Now I put in my USB stick and the USB drive in the same computer and boot from the USB memory stick.

I installed the package mdadm on the stick using Synpatic Package Manager.

I also found that the Ubuntu found several partitions on the NAS disk I try to rescue. You can actually mount these partitions by just clicking on them in Places->partition. In one partition I found a file /etc/mdadm.conf. I copied this data to my real /etc directory.

At this point I rebooted the machine to allow the USB stick Ubuntu recognize the raid drives.

On the next boot I found a new device called /dev/md0. On this device I run the xfs_check. It showed lots of errors. It was obvious that small areas of my disk were really damaged and xfs_repair could not run.

So I mounted the filesystem

```

mount -t xfs /dev/md0 /mnt

```The command

```

cd /mnt
ls

```showed that there were still lots of good directories on the disk.

So I just started to move the data to USB one root directory at a time.
(The /media/disk is my new USB disk drive)

```

tar cf /media/disk/videos.tar --ignore-failed-read videos
tar cf /media/disk/photos.tar --ignore-failed-read photos
...

```Fortunately I have only around 400G of data on the disk so this process will take all day. After dumping data for some 3 hours I found out that I only have a few broken files 99.999% is ok. But still the LaCie NAS software showed only empty folders.

I just wanted to share this if someone else has a similar situation and does not know what to do.

I now have a few hundred gigabytes of data saved. Still some directories to go.

Edit:

After succesfull saving of most data my next task is to fix the LaCie NAS. I found out that the 2nd /dev/sdb was where all hw errors were. So I bought a new 500G drive and downloaded dd_rescue to my stick.

Then I put the new empty drive in the 1st place and keep the original 2nd drive (the broken LaCie 2nd drive in the 2nd slot).

```

dd_rescue /dev/sdb /dev/sda

```will now copy all the data from the broken 2nd drive to my new drive.

After this I put in the original LaCie 1st drive and my new 2nd drive.

```

xfs_repair /dev/md0

```should now be able to run and restore the filesystem to an usable state so I can continue using it as my main storage.

--
Regards,

Karri

---

### Post by ali.king on 2010-09-14
I have one of the blighters - the lacie network space (1 disk, 1 TB)

it stopped working - i.e. not present on the network, not show as connected according to my router, very brief spin up, then just sits there with it's blue light doing nothing

I had tried to upgrade the firmware (1.18 i think) and can remember it say '...yep, all fine...'

after it first stopped responding I had to re-boot it, by pulling the plug, as the power off switch no longer, err, powered it off.

have followed the advice or re-starting within a few seconds to try to reset the device - but all to no avail

so, 7 kitchen knives later, I managed to extract the disk (the single disk, not the 2 500gb ones) and plugged it in to a sata->usb adapter, and then into a laptop running ubuntu.

but it doesn't mount anything, or show any additional devices to mount, running sudo fdisk -l, both before and after plugging the usb lead in, reports exactly the same results

running sudo ls -lsa|grep disk in /dev however, does report and sdb and an sg2.

anyone got any suggestions?

cheers ali...

---

### Post by ali.king on 2010-09-16
in case it helps anyone else, with the help of this post in particular:
[http://forum.nas-central.org/viewtopic.php?f=221&t=1902&start=30](http://forum.nas-central.org/viewtopic.php?f=221&t=1902&start=30)

I found that it was the log file that had filled up one of the partitions.

so I have my data back - phew, but less confidence in this drive than ever

---

