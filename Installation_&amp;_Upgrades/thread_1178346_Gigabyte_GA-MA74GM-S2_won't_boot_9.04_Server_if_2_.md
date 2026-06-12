---
title: "Gigabyte GA-MA74GM-S2 won't boot 9.04 Server if 2 drives connected"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by ZenRunner on 2009-06-04
I have a Gigabyte GA-MA74GM-S2 motherboard (rev 2.0 with latest BIOS version FB) with an IDE DVD drive and 2 SATA hard drives connected and no matter what I try, I am unable to get Ubuntu 9.04 Server (64 bit) to successfully boot if both SATA hard drives are connected.  When I try to boot, I get the message:

ALERT!  /dev/disk/by-uuid/af0de554_9d86_4e14_b506_9c7139a74ee9 does not exist. Dropping to a shell!

and then I get dropped into BusyBox.

When I poke around, I see that there is no by-uuid directory set up under /dev/disk but instead there is an isw_ccjdbbjbig_Volume_0000 directory set up under /dev/mapper.

However, if I disconnect the second drive, the system boots just fine and I see the correct by-uuid directory set up and no isw_ directory set up under /dev/mapper.  In both scenarios, I see "softreset failed (device not found)" and "no block devices found" messages but since the system is able to boot with those messages and 1 drive connected, I'm assuming that's not relevant to my problem.

I've tried installing with the hard drives set to IDE and AHCI and I get the same result.  I've also tried installing with and without LVM with the same result.  As well, I've checked the boot order of the hard drives to make sure the Ubuntu one is first.  The other hard drive is unpartitioned.

I also tried installing as RAID1 using the software RAID at one point.  When I tried booting afterwards, I got a message that the RAID array was degraded and I only had access to one of the drives.  I gave up on that but made sure to not only zero the superblocks afterwards, but also to completely wipe the drives with zeroes.

I've Googled my fingers off and have tried things like adding rootdelay=120 and nodmraid options to my Grub kernel options, disabling devices in the BIOS, etc. but nothing has worked.

I believe that the problem is that either the BIOS is incorrectly reporting on the devices or Unbuntu is misinterpreting what the BIOS is reporting.  Whatever the problem is, at this point I'm stumped.  Does anyone know what's happening, and how to fix it?  Thanks.

---

### Post by cariboo on 2009-06-04
Have a look at the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto"), it should help you solve your problems.

---

### Post by ronparent on 2009-06-04
I have been finding that 9.04 will not automatically activate and mount raids. Can you manually activate and mount the raid array after booting. If so, I recommend dropping back to 8.10 where the problem doesn't exist.

---

### Post by ZenRunner on 2009-06-04
Thanks for the replies so far.

At this point I'm just trying to get a simple single disk install working, not RAID 1.  If I only have 1 disk connected, everything is fine but if I connect a second (empty) disk, I can't boot anymore.  It doesn't matter whether the second disk is connected during the install process or not.

I believe that when I have 2 disks connected, Ubuntu is trying to set up a dmraid isw array at boot time for some unknown reason.  After my early attempt to set up a software RAID 1 array, I did run KillDisk to completely zero out the drives to ensure I was starting fresh again.  Very strange . . .

---

### Post by ZenRunner on 2009-06-04
OK, I'm getting closer to getting to the bottom of this.

I just tried using a different (never used) drive as the second drive and everything booted up fine.  Which means that the problem is that the 2 drives that I originally used for my RAID 1 experiment still are somehow marked as being part of a RAID 1 array. I did zero the superblocks of every partition on both drives and then ran KillDisk to completely zero the drives but apparently that's not enough.  What do I need to do to remove all traces of my previous attempt to create a RAID 1 array on these drives?  Thanks.

---

### Post by ronparent on 2009-06-04
I'm not as familiar with mddam syntax as with dmraid, but if metadata for raid definition has been written to the drives I would imagine that mddam could erase it. Also if you have no further need of the software raid try uninstalling mddam. Then nothing would remain on the system to act on any data that might remain on the drives.

---

### Post by ZenRunner on 2009-06-11
Thanks for the replies!

I finally did resolve my problem by going back and setting up a software (mdadm) RAID 1 array again and then troubleshooting the problems from that point.

The mdadm related problem I was having was that after finishing the install and rebooting, I got the "There appears to be one or more degraded RAID devices" message followed by a question if I wanted to boot the degraded array.  I finally figured out why this is happening and how to fix it.

In my case, the problem was that the "dmraid" fakeraid driver was being loaded in addition to mdadm, even though my SATA drives weren't set to RAID in my BIOS and I said not to configure RAID devices when the installer detected my motherboard RAID capability during the install process.  The dmraid driver made my 2 disks look like a single RAID 1 array, and then when mdadm tried to find the 2 disks it only found the 1 array being presented by dmraid, causing the error message.

Getting to the bottom of the problem was hard but the fix was fairly easy - remove dmraid, reboot, and fix the mdadm RAID arrays if necessary.

To remove the dmraid package, type:

```
sudo apt-get autoremove dmraid
```After you've done this, reboot the system and check on the status of your mdadm RAID arrays by typing:

```
cat /proc/mdstat
```You can also run the command:

```
sudo mdadm --query --detail /dev/md*
```to see more info about your RAID arrays.

If any of your arrays are degraded, you can add back the missing disk by typing a command like:

```
sudo mdadm /dev/md0 --add /dev/sdb1
```which in my case added the first partition of the second hard drive (/dev/sdb1) back into my first RAID 1 array (/dev/md0).  You'll have to modify the command as needed for your own system.

Then, once your array(s) have finished rebuilding, you should be good to go!

---

