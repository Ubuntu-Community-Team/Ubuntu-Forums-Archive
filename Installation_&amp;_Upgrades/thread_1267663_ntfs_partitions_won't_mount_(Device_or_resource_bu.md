---
title: "ntfs partitions won't mount (Device or resource busy)"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by patsissons on 2009-09-16
i have looked around the forums for this problem and found several solutions, but none have worked so far.  Here are the details of this problem:

I re-installed ubuntu jaunty on my linux drive.  I wanted to keep things as close to the same as they were before, so i only reformatted the the root partition, everything else was left alone, other than set as mount points.  The install detected my ntfs partitions fine (2 partitions on 2 drives) and added them to grub's menu.

Now when i boot into linux, the ntfs partitions are (kind of) missing after booting.  By that i mean that the partitions are visible from running fdisk -l, but there are no actual dev nodes affiliated with these partitions.  This means that fdisk -l will show a proper entry for /dev/sda1 but /dev/sda1 does not actually exist.  I can however open the drive in fdisk and (re)write the partition table which will cause the kernel to re-read the disk and create the dev nodes.  At this stage, i can now attempt to mount it (through fstab, manually with mount, or with ntfs-3g).  All methods of mounting result in the following error message

"fuse: mount failed: Device or resource busy"

Here are some solutions i have tried...

* partition is damaged?
>> sda1 contains a windows XP install and booted fine from grub

* partition has errors?
>> ran chkdsk /F from windows and repaired any errors, problem still exists

* partition is not valid ntfs?
>> `ntfs-3g.probe --readwrite /dev/sda1` returns 0 (volume is mountable)

* something missing on system to mount ntfs partitions?
>> while 2 of my drives are not mounting, a 3rd removable bay drive with an ntfs partition on it mounts without trouble

* disk is damaged?
>> ran testdisk on sda1 and reported no problems with disk or partition on the disk

------------------

So now i am confused, what could be the cause of this?  syslog suggests nothing bad happening at boot time, so i am out of ideas.  Any suggestions?

Thanks.

---

### Post by stlsaint on 2009-09-16
i will subscribe to this thread and continue to help as i must go right now...but do this for reference.
go to [BootInfoScript]("http://sourceforge.net/projects/bootinfoscript/") and download the script. 
run this in terminal:

sudo bash ~/Desktop/boot_info_script*.sh

it will but a RESULTS.txt on your desktop...upload that .txt file here so we can see your setup in its entirety.

---

### Post by patsissons on 2009-09-16
i actually kept searching around on this problem all night tonight and did find the answer eventually.

What happened i guess, is that my drives (for whatever reason) had raid metadata stored in the partition table (not sure why, i haven't used either for a raid setup in the past).  i believe running `**dmraid -n**` will display any raid setups detected.  To correct the problem, i just stripped the raid metadata from the disks

```

# disable the raid setup
dmraid -an
dmraid -si

# remove the metadata
dmraid -E -r
```

this effectively releases the hold on the device node, and allows mount to get a lock on the device node (and subsequently mount it).  I would definitely put this into the obscure pile, but who knows maybe someone else will get some use out of this!

after running the above commands i was able to simply run `mount -a` and my ntfs partitions were mounting properly!

---

### Post by raucous1 on 2011-05-14
Thanks, this solution worked for me as well!

---

### Post by Allleksandar on 2011-06-19
hi
i`m having the same problem here my results tnx for any help i need one
i think i`ve tried anything and nothing help me so far can`t wait for your`s reply and find out what`s the problem with my pc..

---

