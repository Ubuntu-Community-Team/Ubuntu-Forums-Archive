---
title: "FakeRAID / dmraid volume mounting problems"
date: 2009-01-20
forum: Hardware
---

### Post by AzT3K on 2009-01-20
Hi everyone,

First of all I'm relatively experienced windows user, but new to linux / ubuntu so please excuse my n00bness.

The machine this is in reference to is a AMD Athlon X2 4200+ on an socket 939 NF4 chipset.  It has 4 x 250 GB SATA II disks arranged in two 500gb raid0 arrays via the RAID bios i.e. fake raid as its an NF4 chipset + requires drivers etc.

I downloaded and installed ubuntu from the AMD64 alternate install iso and the installer dmraid picked up my two stripe arrays - I installed ubuntu to one of them and it partitioned fine into a swap and a file system partition and boots perfectly etc. I know there other ways i could have arranged the partitions that may have been more efficient, but as I'm new i didn't want to over complicate things.

The other array was initially formatted to one 500gb logical drive with an NTFS file system.  

Okay so here's the problem.

Initially nautilus would show a dive called 500gb media but wouldn't mount it at that point the drive had no label so 500gb media was what it was listed as.  In the dev/mapper directory there was a listing for a nvidia_iebhaeae1 - i.e. the first partition on the nvidia_iebhaeae fakeRAID array in question.  I Did my homework and i discovered that I could mount the volume by doing a dirty mount with ntfs-3g via the command:

sudo ntfs-3g /dev/mapper/nvidia_iebhaeae1 /media/Big -o force

It mounted the disk fine and created a "Place" called Big in nautilus in addition to the 500gb media, so i decided to take it one step further and edit the fstab file. i added this line

/dev/mapper/nvidia_iebhaeae1 /media/Big ntfs-3g defaults,force 0 0

That worked all good as well and I ended up with a device in nautilus called Big that contained the contents of the array and no 500gb media was listed.

Upon doing some reading I discovered some of the benefits of the ext3 file system. so i dumped all the contents of the array to another drive on my system, destroyed the partition with gparted, made a new one and formatted to ext3 with the label=Big. 

I rebooted the system and sure enough there was a "Place" in nautilus called big.  when i click on it i get this error:

Unable to mount the volume 'Big'.
>details:
mount /dev/sdd1 already mounted or /media/Big busy

then abut 20 seconds later i get this:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I thought ok, that's pretty much what was happening with the NTFS formatted partition so I tried this:

sudo mount -t ext3 /dev/mapper/nvidia_iebhaeae1 /media/Big

And sure enough I got a second Big in the "Paces" pane in nautilus that worked fine, following the same logic I edited line in the fstab file to:

/dev/mapper/nvidia_iebhaeae1 /media/Big ext3 defaults 0 0

and on reboot the volume mounts, but I still have 2 Bigs listed in the places pane - one works and the other still gives me the same error.

I've tried using LABEL=Big and UUID=the drive id in my fstab file, but still the same result.

There are no other entries in the fstab file for that volume, which means the problem isn't there, at least i think so.

My questions are:

Why is that Ubuntu preemptively provides Big as a drive/media to mount even though the way it sets itself up makes the drive unmountable?

- There are other drives on my system that work flawlessly, i.e. they appear as a Place and they mount when you click on them.  One thing I'll say is that aren't Raid Volumes, so im guessing its something to with the way dmraid is presenting the array to the OS.

Why is it that using NTFS-3G in concert with fstab hides the unmountable version of the place in nautilus where as the ext3 formatted drive appears twice when mounted in the same context?

If I use dolphin to browse my files i get one place that is shown as Big, but dolphin wont let me view it no error it just unselects big - so im presuming its the unmountable version its seeing.


If i change the settings to show all locations i get an additional place called Volume(ext3) if i try to view the contents of that i get an error:

An error occured while accessing Volume(ext3), the system responded org.freedesktop.Hal.Device.Volume.PermissionDenied device /dev/sdc1 is listed in /etc/fstab. Refusing to Mount.

However I can still access the drive by accessing the mountpoint i manually set in the file system through dolphin i.e. /media/Big

Okay at this point I'll post my drive info:

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system>  <mount point>  <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/mapper/nvidia_caghibdf1
UUID=70a97493-c267-4959-b843-defaac350590 / ext3 relatime,errors=remount-ro 0 1
# /dev/mapper/nvidia_caghibdf5
UUID=cdcce6f0-c930-4a5d-bbd6-3bbd97fb1779 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#2ndary Raid Array - ext3
/dev/mapper/nvidia_iebhaeae1 /media/Big ext3 defaults 0 0

sudo fdisk -l:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9eee688

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20023   160834716   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Unable to seek on /dev/sdc

Device arrangement:

/dev/sda - 153.38 Gb - 160gb SATAI drive formatted to ext3
/dev/sdb - 232.88 Gb - 250gb SATAII drive-member of nvidia_caghibdf array
/dev/sdc - 232.88 Gb - 250gb SATAII drive-member of nvidia_caghibdf array
/dev/sdd - 232.88 Gb - 250gb SATAII drive-member of nvidia_iebhaeae array 
/dev/sde - 232.88 Gb - 250gb SATAII drive-member of nvidia_iebhaeae array
/dev/sdf - 111.79 Gb - 120gb IDE drive formatted to ext3
/dev/mapper/nvidia_caghibdf1 - ubuntu filesystem
/dev/mapper/nvidia_caghibdf5 - linux swap
/dev/mapper/nvidia_iebhaeae1 - partition with issues label=Big

sudo dmraid -r

/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sde: nvidia, "nvidia_iebhaeae", stripe, ok, 488397166 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_iebhaeae", stripe, ok, 488397166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_caghibdf", stripe, ok, 488397166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_caghibdf", stripe, ok, 488397166 sectors, data@ 0

So in summary - how do i get this drive to mount properly as an ext3 formatted entity so the system properly understands what it is.  Or more specifically how do I stop the unmountable version from coming up and perhaps confusing dolphin etc.  I can access all of my files etc, its just a bit of a hack job, its messy and there is obviously something wrong with the way its set up.

If anyone can shed any light on my situation its would be greatly appreciated,

Cheers,


Aaron

---

### Post by AzT3K on 2009-01-26
Bump ](*,)

---

