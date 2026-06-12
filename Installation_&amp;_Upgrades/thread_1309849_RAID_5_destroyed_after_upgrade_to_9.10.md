---
title: "RAID 5 destroyed after upgrade to 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Bramo on 2009-11-01
Hi All, I don't know where to start, my large RAID 5 was destroyed after I did the upgrade. A few of the particulars I've noticed are:

- My old /dev/md0 is there, but only has 1 disk instead of 3.
- There is a new /dev/md_d0 which I didn't create. See below:

```
root@zeus:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive dm-2[1](S)
      488383936 blocks
       
md0 : inactive sdd1[2](S)
      488383936 blocks
```

I don't know what the dm-2 is. The members of /dev/md0 should be sdb1, sdc1 and sdd1. My mdadm.conf is as follows:

```
root@zeus:~# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR james@zeus

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1
```

I tried reassembling the array (Including after stopping the new 'phantom' array. One thing I noticed when trying to rebuild was that there are no device files for sdb1 and sdc1 (sdb and sdc do exist) as follows:

```
root@zeus:~# ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb  /dev/sdc  /dev/sdd  /dev/sdd1

```

However, sfdisk does recognise the partitons as raid-autodetect:

```
root@zeus:~# sfdisk -l /dev/sdc

Disk /dev/sdc: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdc1          0+  60800   60801- 488384001   fd  Linux raid autodetect
/dev/sdc2          0       -       0          0    0  Empty
/dev/sdc3          0       -       0          0    0  Empty
/dev/sdc4          0       -       0          0    0  Empty

```

the output for sdb is similar. 

Any ideas what's happened? I think if I could get the device files to come back I could recreate my /dev/md0 and the data would still be intact.

---

### Post by Kokopelli on 2009-11-01
Can you do a "sudo mdadm --detail /dev/md0" and "sudo mdadm --detail /dev/md_d0"?  That should tell us what drives mdadm **thinks** are part of each array.  I remember having a similar problem with one of my arrays.  Unfortunately I do not remember what I did to fix it.  Since it was a new array in my case I might have just wiped and recreated it.

---

### Post by Bramo on 2009-11-01
mdadm --detail doesn't seem to work. It just tells me that each of the arrays is inactive.


Interestingly, after a reboot I have the following for md_d0 (the phantom menace):

md_d0 : inactive dm-3[1](S)
      488383936 blocks

It was dm-2 before. I think the dm is for device mapper, but I don't really know what that is or where it was created.

- My install partition is the default lvm setup from around the 8.10 release and I did have a lvm setup on top of my RAID 5 that's vanished (which is needless to say, vanished).

---

### Post by Kokopelli on 2009-11-01
ok so we need to do this the hard way....

```
sudo mdadm --query /dev/sda1
``` and repeat for each partition that should be part of the array.  What we are looking for is if mapper correctly realizes each are part of the same array.

The output should be something like this:
> 
/dev/sdc1: is not an md array
/dev/sdc1: device 1 in 5 device active raid5 /dev/md0. Use mdadm --examine for detail

Yours will be inactive so the wording will be a little different but you get the idea.

EDIT: I just noticed the dm-3... is this a fakeraid (i.e. a raid set up at bios level)?  Oddly enough there is another RAID problem on the forums right now where it lists md-* devices.  I am not familiar with that device type, I think it is fakeraid but I am not sure.

---

### Post by Bramo on 2009-11-01
The problem is, ubuntu doesn't seem to think there is a sdb1. There is an sdb but no sdb1 (same situation for sdc).

If i do the --query on sdb1 I get "no such file or directory". If I do a --query on sdb it says /dev/sdb: is not an md array (which is actually correct).

I seem to be stuck unless I can get my devices to show up. The strange thing is that sfdisk and even gparted can see the linux raid partitions (sdb1 & sdc1) on the disks respectively (sdb and sdc).

I'm really confused.

---

### Post by Kokopelli on 2009-11-01
> **Bramo said:**
> The problem is, ubuntu doesn't seem to think there is a sdb1. There is an sdb but no sdb1 (same situation for sdc).

If i do the --query on sdb1 I get "no such file or directory". If I do a --query on sdb it says /dev/sdb: is not an md array (which is actually correct).

I seem to be stuck unless I can get my devices to show up. The strange thing is that sfdisk and even gparted can see the linux raid partitions (sdb1 & sdc1) on the disks respectively (sdb and sdc).

I'm really confused.


We are getting out of my realm of experience but it looks like sda and sdb are part of a fake raid.  dmraid would be the function to control those but by what you are saying the raid is a software level one.  I took a look at the man page for dmraid (I have never used it)...

try "dmraid -r" if it responds back with raid devices then the system at least thinks they are there.  so try "dmraid -an" to deactivate all fakeraids.  Maybe then your missing drives will show up?  I am sort of driving blind here so sorry I can not be more specific.

---

### Post by Bramo on 2009-11-01
Thanks, you seem to be on the right track. I think the problem is that my motherboard has two SATA ports so some of my hard drives are on a SATA PCI card that supports fake raid.

It would seem that dmraid automatically wants to control these (and seems to be responsible for md_d0 somehow).

Didn't have any luck with dmraid. I think if I can disable/uninstall this then my software raid should work again. Thanks for all you help so far, appreciate any further tips on getting there. Google isn't giving up much.

---

### Post by Cr0n_J0b on 2009-11-01
check my threads, they are in this forum.  I'm actively trying to fix this exact situation.  I've asked the mods to sticky a note to anyone using mdadm.  

here's what I think is happening.

if you are like me and you have onboard SATA, maybe with raid support...then there is a new "feature" of 9.10 that turns on DMRAID.  you can look that up, but it's basically the support for fakeraid, to help you run raid disks that you assign in the bios.  

The problem is that it grabs the device ID and I think even writes over the partition table.  In my case, it blew up all of my arrays. (3 of them).

I was lucky enough to have a backup and to have not installed an old backup array.

I have no idea how to specifically fix this to make an old array work.  I'm having enough trouble now just building a proper array and making it stick through a reboot.

---

### Post by Bramo on 2009-11-01
I found one these instructions on removing dmraid:

[http://atlanticlinux.ie/blog/?tag=dmraid](http://atlanticlinux.ie/blog/?tag=dmraid)

Hopefully they'll work and I'll get my data back. My raid is a home media server I can't possibly back up so fingers crossed.

---

### Post by Kokopelli on 2009-11-01
I have done some reading and found this:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/392510](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/392510)

the take away I got from it is you moght try the "nodmraid" boot option.  The maintainer did not seem to like the solution but I think it would do what is needed for you.

---

### Post by Cr0n_J0b on 2009-11-01
If you are like me...you won't be happy with uninstalling DMRAID.  I tried...

1) uninstalling it after it fresh 9.10 install (package manager)
result:  SYSTEM WON'T BOOT
2) instaling 9.10 with NODMRAID
result:  SYSTEM WONT INSTALL (no partitions)
3) go to liveCD, remove DMRAID, then install...
result:  DMRAID is used in the partitioning system, so no go there.
4) move boot drive out of the nvidia scope, to SI chipset
result:  still seen as nvidia devices

I finally just decided to live with it.

what chipset are you using?  what motherboard?

---

### Post by Bramo on 2009-11-01
Indeed, boot option did the trick. RAID data unaffected once I got rid of dmraid.

I would strongly suggest anyone successfully using software raid do not upgrade. If you do want to upgrade this would be the prudent approach.

- back-up raid data (as always, if possible).
- after install, before restart add nodmraid boot option (see below).
- restart and uninstall dmraid (paranoid in case future kernel ignores option).

In order to set nodmraid, edit /boot/grub/menu.lst as root (sudo) so that nodmraid is at the end of the kernel line as shown below:

```

title		Ubuntu 9.10, kernel 2.6.31-14-generic-pae
root		(hd0,0)
kernel		/vmlinuz-2.6.31-14-generic-pae root=/dev/mapper/zeus-root ro quiet splash nodmraid
initrd		/initrd.img-2.6.31-14-generic-pae
quiet
```

Then run "sudo update-grub".

As I said above, I would also suggest uninstalling dmraid "just in case".

---

### Post by Cr0n_J0b on 2009-11-01
OK, 

I'm glad this worked for you, but I don't think that I can do this.  The reason is that my boot volume is on one of the fake RAID partitions...though it's not fakeraid, it's just a single disk.  but if I shut off dmraid, then I would guess that it won't be able to find my boot disk.

can you tell me what device your boot drive WAS on?  mine is something like nvidia_dbbagcfc1 or something in /dev/mapper/

---

### Post by Bramo on 2009-11-01
Sorry Cron_Job,

I didn't see your post before my last update. Not sure about motherboard, msi socket 775 is about as much as I can remember. The 'fake raid' causing the problem was on a little 4 port SiS chip PCI SATA card with software raid support.

In my case once I prevent dmraid on boot (as detailed above), I was able to uninstall dmraid without a hitch.

---

### Post by Bramo on 2009-11-01
Ummm, I'm not sure. My stupid phantom raid thing was on device mapper sis_xxxxxxxxxx or something.

I can't see a way out if it's ended up putting your boot partition on a fake raid. Luckily my boot partition isn't raided at all. Just my media files. Ironically, to give me some security because they're too big to back up!

---

### Post by Kokopelli on 2009-11-01
> **Cr0n_J0b said:**
> OK, 

I'm glad this worked for you, but I don't think that I can do this.  The reason is that my boot volume is on one of the fake RAID partitions...though it's not fakeraid, it's just a single disk.  but if I shut off dmraid, then I would guess that it won't be able to find my boot disk.

can you tell me what device your boot drive WAS on?  mine is something like nvidia_dbbagcfc1 or something in /dev/mapper/

If you are not using fakeraid for windows or linux then nodmraid will not be harmful. It should eliminate the /dev/md-# blockdevices which is what you want as the first step to fixing your problem.  If you are using fakeraid (such as in windows) then we should exhibit more caution since you could potentially really screw up that raid if you accidently mount one part of the unrecognized bios level raid.

---

### Post by Cr0n_J0b on 2009-11-01
> **Kokopelli said:**
> If you are not using fakeraid for windows or linux then nodmraid will not be harmful. It should eliminate the /dev/md-# blockdevices which is what you want as the first step to fixing your problem.  If you are using fakeraid (such as in windows) then we should exhibit more caution since you could potentially really screw up that raid if you accidently mount one part of the unrecognized bios level raid.

I would love it if that were the case.  He's what I think, based on my testing....

nvraid based chipsets are reporting ALL devices to be fakeraid.  When I tried to disable dmraid, the partitions were not visible to the installer at all.

I'm guessing that if I boot with nodmraid, grub will get stuck looking for my block device at nvidia_dbdchcfc1, when it's not there anymore. With DMRAID gone that device will be renamed as sda1.

that's my guess anyway.

As I've said, i tried to install using the exact kernel flag nodmraid, and when i get to the partioner it shows no storage devices at all, so there is no where to load the OS>

---

### Post by Kokopelli on 2009-11-01
> **Cr0n_J0b said:**
> I would love it if that were the case.  He's what I think, based on my testing....

nvraid based chipsets are reporting ALL devices to be fakeraid.  When I tried to disable dmraid, the partitions were not visible to the installer at all.

I'm guessing that if I boot with nodmraid, grub will get stuck looking for my block device at nvidia_dbdchcfc1, when it's not there anymore. With DMRAID gone that device will be renamed as sda1.

that's my guess anyway.

As I've said, i tried to install using the exact kernel flag nodmraid, and when i get to the partioner it shows no storage devices at all, so there is no where to load the OS>

I am out of ideas then, sorry.  Maybe file a bug or look for an existing one on launchpad?  (I did a quick search and did not find one.)

---

### Post by Bramo on 2009-11-01
Thankyou both for your help.

Cron_Job, I'm not sure what your next step is either. I don't know the inner workings of this stuff at all.. 

Maybe it would work to connect just one disk and install to that. dmraid shouldn't interfere then as far as I can tell.

Once installed disable and uninstall dmraid as worked for me. Then connect your other disks and configure software raid.

Bit of a fiddle but may get you up and running.

---

