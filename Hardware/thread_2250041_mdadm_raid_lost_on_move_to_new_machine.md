---
title: "mdadm raid lost on move to new machine"
date: 2014-10-26
forum: Hardware
---

### Post by jarek6 on 2014-10-26
First things first, here's some background information as to my situation. My desktop has been running Ubuntu 12.10 for the past several years and I'm looking into finally updating to something more recent. This machine has also served as my File/Media server and first I want to move the server functionalities to a new machine that I've built. The new machine runs Fedora 20 (this was the first distro I could get to actually work with the ASRock C2550D4I motherboard that's powering the thing), and from what I've researched moving the mdadm raid should be as simple as moving the drives and reassembling it in the new machine. Sadly the new server doesn't see the raid array and rather than try to investigate thoroughly I moved the raid back into the original Ubuntu box, with the intent of making a full backup and then recreating the array on the new server. This is where my story starts.

 Upon plugging the raid back into its original box, the Ubuntu machine doesn't see the raid array either. Under /dev/ I can see the nodes for each of the hard drives, but the raid partition doesn't appear on any of the drives so I can't assemble the raid. It's been so long since I've created the raid, so I'm not sure how exactly I went about doing it. I can't remember if I just left the disks blank and told mdadm to do everything (could explain why there are not "proper" partitions, or if I created the partitions and then told mdadm to use the partitions I created. Thinking about it now, and given what I'm seeing I'm inclined to think the former.
On the Ubuntu box the raid drives appear as sdc, sde and sdf and . All three are in the same boat and so I'll only include information for sdc.

First off, the /dev
```

cancech@My-Universe:~$ ls /dev/sdc*
/dev/sdc

```

 Fdisk however does see the partition:
```

cancech@My-Universe:~$ sudo fdisk -l /dev/sdc
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
 Partition 1 does not start on physical sector boundary.

```

mdadm also seems to see something:
```

cancech@My-Universe:~$ sudo mdadm -Evvv /dev/sdc
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

```

I can't recreate the array:
```

cancech@My-Universe:~$ sudo mdadm --assemble --scan
mdadm: No arrays found in config file or automatically
cancech@My-Universe:~$ sudo mdadm --assemble /dev/sdc /dev/sde /dev/sdf
mdadm: device /dev/sdc exists but is not an md array.

```

Here's what dumpe2fs has to say
```

cancech@My-Universe:~$ sudo dumpe2fs /dev/sdc
dumpe2fs 1.42.5 (29-Jul-2012)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdc
Couldn't find valid filesystem superblock.

```
[HR][/HR]
The array was formated as EXT4 and was working beautifully prior to the move. I've been bashing my head against this problem for the past two weeks and given what I've found on the interwebs I've tried doing the following

* Remove Intel fakeraid signatures from the drive
```

cancech@My-Universe:~$ sudo dmraid -r -E /dev/sdc
no raid disks and with names: "/dev/sdc"

```

* Tried booting with nodmraid option in grub (couldn't figure out how to update grub.conf so I manually updated the boot entry while at boot time to include the nodmraid option).

* Tried zeroing out the superblock
```

cancech@My-Universe:~$ sudo mdadm --zero-superblock /dev/sdc
mdadm: Unrecognised md component device - /dev/sdc

```

[HR][/HR]
There's only one last thing that I've come across, but haven't as of yet tried to do which is to force create the raid array
```

mdadm --create /dev/md0 -v -f -l 5 -n 3 /dev/sdc /dev/sde /dev/sdf

```

 I haven't tried doing this out of fear that the "create" would nuke the current raid and I'd end up losing everything from within. It's not a big deal if it comes to that (I made a backup of all of the important stuff off of the array prior to trying to move it), though I'd rather not lose anything if I can avoid it. Would it destroy anything, or would it "recreate" the array in ways that a simple "assemble" has been unable to?

One last thing to add, the raid array has been auto-assembling for me on boot-up via an entry in /etc/mdadm/mdadm.conf, and due to no small stupidity on my part I've deleted that config and can't check what it had been doing for the past several years. 

If there is someone more knowledgeable about mdadm that could provide some insight into what I'm seeing, then I would greatly appreciate any and all help :) 

Thanks!

---

### Post by weatherman2 on 2014-10-26
What are the partitions that are part of the RAID?  That is, it should be /dev/sdc1 /dev/sde1 etc. (which are partitions) not /dev/sdc /dev/sde (which are devices on which partitions exist).

---

### Post by jarek6 on 2014-10-26
Yes, the partitions would be sdc1, sde1, sdf1. Only a single partition would exist on these drives and that would be the one used for the raid.

---

### Post by weatherman2 on 2014-10-26
So did you try issuing mdadm with the partition references (/dev/sdc1) instead of the disk reference (/dev/sdc) ?

---

### Post by jarek6 on 2014-10-27
I have tried doing that, and no success there.

```

cancech@My-Universe:~$ sudo mdadm --assemble /dev/sdc1 /dev/sde1 /dev/sdf1
mdadm: cannot open device /dev/sde1: No such file or directory
mdadm: /dev/sde1 has no superblock - assembly aborted

```

---

### Post by jarek6 on 2014-10-30
Any other ideas?

---

### Post by Ben_Fischer on 2014-12-18
Did you find any solution yet? 

I got nearly the same Problem.

I've had my UBUNTU-NAS working for years, using a RAID5 as storage (7x 2TB). I built it once using OPENMEDIAVAULT, which didn't create any partitions on the single disks. Migration to UBUNTU was no Problem, even one earlier mainboard-change in the past made no problems.
When I changed the mainboard to C2550d4i yesterday, the system wasn't able to recognize three of the disks as RAID-members. These three disks are two WD20EARS and one WD20EADS which have a GUID partition table. The four other disks are HGST disks with MBR and they are recognized as RAID-members.
I already tried the different SATA controllers with no success - my next step will be to change back to the old mainboard, hoping it will work.

It seems, that only GUID disks are affected. I didn't change anything on the disks, so i hope, my data is still there. I have backups of most important data, but not all of it. :-(

Any ideas?

---

