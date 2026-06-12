---
title: "Problem booting from software RAID with LVM"
date: 2008-10-11
forum: General Help
---

### Post by VSpike on 2008-10-11
Hi. I had a system with /boot as a real partition and everything else in LVM.  This was working fine.

Then I added a new pair of disks, and created a software RAID 1.  I put LVM on top of this.  That was also working fine.

Then I moved my / partition from the original LVM to the one on the RAID.  I've updated menu.lst, but when booting the system stops while waiting for the root FS, and drops into busybox.

In busybox, cat /proc/mdstat shows no RAIDs running so I tried "mdadm --assemble --scan" which is what I have to do in the live CD to get the raid started, but I get the errors:-

mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: No arrays found in config file or automatically

I'm sure this a problem with my initramfs, but how can I fix it?

---

### Post by VSpike on 2008-10-11
Slight progress.

If I manually assemble the RAID sets at the busybox console, that works, e.g.:

mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
mdadm --assemble /dev/md1 /dev/hda1 /dev/sda3

Then I checked pvscan and it shows my physical volumes, so I hit ctrl-D and the system boots fine.

So, why can mdadm not find the raids automatically?  The config file in the initrd is the same as the one in my real /etc/mdadm/mdadm.conf in that it doesn't specify the devices but uses the "partitions" keyword to scan all parititions.  All of them use persistent superblocks.

Should I add definitions of existing arrays to my mdadm.conf?  Does this file get copied verbatim to the initrd, or is that one generated independantly?

---

### Post by fjgaude on 2008-10-11
I'm not sure but you may have a "race" issue here... it the **md** in the kernel that does the assemble at boot time, not **mdadm**. If the kernel needs anything from the array before it is assembled then the boot process has to halt.

Thinking along these lines may help in finding a solution with your situation.

---

