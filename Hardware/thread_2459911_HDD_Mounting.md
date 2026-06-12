---
title: "HDD Mounting"
date: 2021-03-29
forum: Hardware
---

### Post by Robk29 on 2021-03-29
Hi,

I just built a new system which went very smoothly until now. I am running Ubuntu 20.04 and booting off an SSD. The last step for me was to install a HDD and I managed to figure out how to use Gparted to create one large partition in FAT32 (I also have Windows systems). 

The problem: I can see the disk via 'Disks' and even write new files to it, however despite several attempts I cannot mount it properly at startup and even screwed it so badly at one stage that I somehow lost permissions! And had to start again.
The details: Device = '/dev/sdb1', UUID = '3598-3DAE', Partition type = 'Basic Data' and Contents = 'FAT (32-bit version) &#8212; Mounted at /media/rob/DATA'.

Based on the information above, could someone please advise the commands that might solve this? Very frustrating as I can hear that slab of metal spinning.

Thanks

---

### Post by CelticWarrior on 2021-03-29
FAT32 is probably the worst filesystem for large partitions, it was never meant for that. Of course, it depends on how large... But anyway it's dumb to use FAT32 when you can use NTFS for a data partition shared with Windows. Backing up (if needed) and reformatting to NTFS (supports large partitions AND larger then 4GB files) is therefore the immediate logical suggestion.

If you want any additional data partition, regardless of filetype, to be mounted automatically then you can do the traditional way by editing fstab or using Disks > Edit... Turn off the default, select mount at boot and adjust the other fields properly. It's that simple.

Of course, for any dual-boot scenario, irrespective of additional shared partitions or even if Windows is the only OS, the Windows Fast Startup feature should be disabled. If sharing a data partition then "should" turns into "must", absolutely.

---

### Post by Robk29 on 2021-03-30
Thanks for the suggestion. I changed the partition to NTFS and mounted the drive.

20.04 doesn't seem to come with full disk encryption by default like it once did so FAT32 would have tripped me up with Vera-crypt given the size restrictions, so thanks again. I find when building a new system you focus so much on the hardware you lose some visability.

---

