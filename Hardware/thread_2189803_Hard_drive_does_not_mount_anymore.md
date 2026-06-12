---
title: "Hard drive does not mount anymore"
date: 2013-11-24
forum: Hardware
---

### Post by acradon2 on 2013-11-24
Hi there, 

I have had this problem before but it went away on its own. I recently updated my computer and reintsalled ubuntu (12.04 LTS) on my main hard drive. I use a second harddrive for all my files. I mounted the drive and added fstab 
/dev/sdb1    /media/mydrive    ext3    defaults    0    0

I chose a 0 at the end to not have the computer take ages to check the hard drive everytime. So far so good. It worked. Until today. I booted the computer and it says that it can't mount this drive. I can either press s to skip or M to manually recover....
I have no idea how to manually recover the drive or mount the drive from there. 

I tried 

sudo mount /etc/sdb1 /media/mydrive

but it says that sdb1 does not exist.

What to do??

Thanks

Acradon

---

### Post by The Cog on 2013-11-24
First thing is to run the command
```
sudo parted -l
```
to see what disks and partitions the computer thinks do exist.

---

### Post by acradon2 on 2013-11-24
This is the output

Model: ATA ST31000524AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext3


Model: ATA ST3500320AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  3754MB  extended
 5      496GB   500GB  3754MB  logical   linux-swap(v1)


So if I read this correctly the disc is now /etc/sda (the hard drive in question is the 1TB drive)

Should I now change the fstab to read /etc/sda ??

Acradon

---

### Post by The Cog on 2013-11-24
That's odd. /dev/sdb1 does seem to exist so the mount command should have worked. I don't understand that.

As for sda nad sdb swapping places, that can happen these days, it depends on the order in which the disks are discovered during the boot process. This is why the normal thing these days is to quote a UUID (which is set in the partition at the time it is formatted) rather than a device number in the mount command. 
Here's a copy of my fstab for instance.```
# / was on /dev/sda6 during installation
UUID=e6eae395-86fd-44e9-84fd-8633c42f038d /               jfs     errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b486350a-6335-4506-a89c-1f0faf9a026b none            swap    sw              0       0
UUID=47b73c6c-f946-4dea-93a5-173740a1a025    /home           jfs   defaults  0       2

```

You can find the UUIDs with the command
```
blkid
```

---

### Post by steeldriver on 2013-11-24
If I'm reading it correctly, the *system* could not mount /dev/sdb1 on /media at boot - probably because it was already mounted as the system drive (due to the mix of UUIDs and /dev/sdXX notation in your fstab, as mentioned by The Cog)

Then you tried to manually mount /**etc**/sdb1 - which obviously is not what you meant (hence the 'does not exist' message)

Regardless, The Cog's prescription should fix things

---

### Post by xeddog on 2013-11-26
The computers I am using have options in the BIOS setup to set the order of the drives.  I don't know why the order would have changed, but you might check that out.

X

---

### Post by acradon2 on 2013-11-26
OK, so I changed the /dev/sdb in the fstab to the UUID and it seems to work. Thanks for the advice. 

Acradon

---

