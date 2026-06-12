---
title: "Please help me understand devices + RAID + udev at boot"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by ultralame on 2008-01-08
I have been having a RAID5 problem for a while that I thought could be fixed with a UDEV rule, but now I am not so sure.  So before I do anything, I was hoping someone could help me understand what's going on...

I have two RAID5 arrays that exist on one set of physical disks.  The drives are partitioned to create md0 and md1.  The arrays consist of the 4 data partitions + 1 parity + 1 spare.

There are 7 SATA disks on my system, A-G (I will use capitals to denote physical disks).  ABCD are plugged into the MB controller and EFG are plugged into a PCI drive controller.

When I created the array, the system booted such that A mapped to sda, B to sdb and so on.  The boot drive (not part of the RAID) is drive A, so I created the array from sd[bcdef] and then added g as a spare with a separate command after assembly.  No problems at first.

When I upgraded from dapper->Edgy->Feisty->Gutsy, I started to have trouble.  Even though GRUB sees the boot partition on (hd0,0), the system scans the auxiliary drive controller first.  So now E->sda, F->sdb ... and my boot drive is sdd.

I dealt with fstab by changing to UUIDs.  This was no problem.

The RAID system self-assembles at boot; and if I disconnect the spare, there is no problem.  All the superblocks seem to be OK, etc.

The problem is that if the spare drive is connected at boot, md will SOMETIMES assemble with the spare partition rather than the correct partition.  In this case it sees 4 good drives + 1 degraded and immediately starts to rebuild on the spare drive.  The next time I boot it will assemble with a different set of drives and essentially rotate the spare around.  Note that when this happens, I always get a "Spares Missing" message and need to manually add the spare drive, even  though I specified the spare in the creation statement.

In fact, yesterday the system assembled md0 from one set of partitions (sd[abcef]1) and md1 from sd[gbcef]2)!  In this case, md0 was the same as last boot so it came up OK, but md1 was degraded and immediately began rebuilding.  This is actually very annoying, as I now need to re-add the spare for each array, and then purposely degrade one of the arrays to get them back where they should be.

Some people told me to use UDEV to write rules to change how the drives get mapped.  But as far as I can tell 1) I can't use UDEV to change /dev/sda (etc), only to add "/dev/alias" and 2) the drives are assembled as soon as they are discovered by the kernel and assigned to their nodes, whereas UDEV runs later on AND 3) the raid is assembled using superblocks, not the device names, so it should not matter.

So questions:

1) Why is my system discovering drives in a funny order?  How come GRUB finds the boot partition on hd0,0 but that ends up mapped to sdd1 when the system actuall boots?

2) Is there anyway to correct this?  That is, can I force a specific drive to be loaded as sda, etc?

3) Is the above problem causing my RAID error?

4) If not, why is the RAID system essentially rotating in the spare each time?  Just thinking out loud, should I (after syncing up the arrays), remove the spare from the arrays, delete the superblocks and then re-add it?  Does mdadm NOT write the superblock to a spare until it's used?  I guess that could be the answer- that md_mod does not expect to find a superblock on a spare?

OK.  I know that's a lot.  Thanks for any help!

---

