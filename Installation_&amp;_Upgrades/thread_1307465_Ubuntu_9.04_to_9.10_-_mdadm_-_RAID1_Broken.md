---
title: "Ubuntu 9.04 to 9.10 - mdadm - RAID1 Broken"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Ben Ab on 2009-10-31
I've been using 9.04 and earlier and have setup a couple of disks with a mdadm RAID1 setup. Until last night this has worked fine.

Then, I upgraded to 9.10. The RAID array (md0) is still active:

Personalities : [raid1]
md0 : active raid1 sde1[1] sdd1[0]
      976751872 blocks [2/2] [UU]

But, when I try to mount the md0 array in exactly the same way that I have using 9.04 and earlier, I get an error message, and something odd in the 'dmesg':

sudo mount /dev/md0 /media/tdrive

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

EXT4-fs (md0): bad geometry: block count 244187992 exceeds size of device (244187968 blocks)

I tried deleting the array and the superblocks, reducing the size of the partitions then recreating the array. Creating the new array worked, but I have the same problem in mounting the array.

Any ideas?

Otherwise the update went OK with some small hiccups with interactions between apps: updates to 'mythtv' broke the monitoring I was doing with 'monit'. Not a huge deal, but a big enough problem to completely confuse a casual user.

ben

---

### Post by Steve Roscio on 2009-11-06
Hi Ben -

I'm still having problems with my RAID array since upgrading to 9.10, but I noticed something that may be helpful to you. 

I received the same superblock error, and then I noticed that my RAID device changed from /dev/md0 to /dev/md/d0 .  So I changed /etc/fstab to this new device, and updated /etc/mdadm/mdadm.conf by putting a new ARRAY line in it that I got from the output of [FONT=Courier New]mdadm --detail --scan

[/FONT]After a reboot, no more superblock or RAID errors, but my device won't automount on boot.  I do a '[FONT=Courier New]sudo mount -a[/FONT]' and it mounts fine.  Still looking into why it won't automount on boot. 

- Steve

---

### Post by syrou on 2009-11-13
This may help you:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479640]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479640")

Have installed the Jaunty kernel and now it mounts correctly. It's a workaround until the bug is in the Karmic kernel.

---

### Post by walabom on 2010-02-07
Hey Syrou,
could you or someone else help me on the Jaunty kernel installation?
I may be unskilled but I don't have the clear view on how to proceed.

Thanks

---

