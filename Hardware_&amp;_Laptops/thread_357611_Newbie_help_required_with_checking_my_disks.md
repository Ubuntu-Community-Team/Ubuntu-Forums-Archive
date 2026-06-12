---
title: "Newbie help required with checking my disks"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by Nigel Eke on 2007-02-09
I'm really after finding out more about useful utilities for this specific problem, but /any/ help would be appreciated...

I have a possible problem with one or both of my disks.  After a little while (a few minutes) of using Edgy there seems to be something running with continual access to the disk.  I suspect this /may/ be related to the PC having been switched off without a proper shutdown.

There are some things I would like to find out how to check:

a) how to find out particular running processes that are actively accessing the disk (and their amount of disk access).

Perhaps a more important first step though:

b) how can I check the disks themselves?

I have already tried badblocks - none detected...

The disks are /dev/hda1 - the boot disk and has the system's programs installed - and /dev/hde1 - has /home mounted to it.

Reading other posts it appears that fsck will be the program to use however it is recommended not to run fsck on a mounted disk.

1. If I umount /dev/hde1 I get the message that it's busy.  It would seem like I need to be able to recreate /home back on /dev/hda1 in order to check hde1.  Is this the easiest way?

2. Would I even be able to unmount /dev/hda1...?  If so, how?


I *think* my best option would be to boot a live distro in order to check the disks.

Is there any other way, or any other utilities that would help me pin down what may be happening?

Many thanks in advance.

Nige

---

### Post by Nigel Eke on 2007-02-10
> I *think* my best option would be to boot a live distro in order to check the disks.

Okay - I did exactly this and ran fsck on /dev/hda1 and /dev/hde1.  They both came up clean.

At least now I know there's no problem with the hard-drives.  I need to find out which process is thrashing the disk...  and that's for a different foum...

---

