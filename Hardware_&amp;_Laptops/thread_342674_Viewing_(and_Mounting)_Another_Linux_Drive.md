---
title: "Viewing (and Mounting) Another Linux Drive"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by Ingla on 2007-01-20
Hello.

I have two hard disks running in drawers connected to the motherboard. The drawers are for convenience in changing hard drives. They are not USB or other removable media. It's the same as having two hd's in the machine, except that I don't have to open the box to change hard drives.

Typically, I have a Windows drive in one drawer and a Linux one (Ubuntu) in the other. I boot into the one I want by changing the boot sequence in CMOS.

Linux sees my drives as follows:

hda Windows (drawer 1)
hdb CD ROM
hdc Linux  (drawer 2)

If I'm in Linux, I have no trouble mounting the Windows drive. If I put a different Windows hd in drawer 1, I can mount it with the usual commands.

Now I have two Linux hard drives (one with Breezy and a new one with Dapper). I want to be able to transfer files between them.

In keeping with the above arrangement, I installed Linux on both of these hard disks while they were in drawer 2 (hdc1) and were the only drives in the machine. Jumpers are set for Master or Single.

Now, while booted into the Linux drive on hdc1 (drawer 2), I want to put the other Linux drive in drawer 1 (hda1) and mount it. However, the drive I'm in doesn't even see it. Trying various mount commands, including -a or designating an ext3 file system, I'm simply told there's no drive there.

I assume that Linux is looking for the drive's file system on hdc1 because it was installed there. 

Seems strange I can see Windows but not Linux.

Is there anything I can do to make the drive in drawer 1 (hda1) visible and mountable from the drive in drawer 2 (hdc1), preferably without making irreversible changes that will prevent me from booting it again in drawer 2 (its proper home)?

Any help appreciated.

Thanks

---

