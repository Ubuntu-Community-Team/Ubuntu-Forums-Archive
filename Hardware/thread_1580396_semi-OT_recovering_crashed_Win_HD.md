---
title: "semi-OT: recovering crashed Win HD"
date: 2010-09-23
forum: Hardware
---

### Post by the_jest on 2010-09-23
A friend of mine has a Dell laptop running Windows XP, whose HD contained about 200GB of important and (of course) non-backed-up data, on a 250GB SATA drive. While the computer was (of course) on, she moved it and dropped it onto a table, and it would no longer boot, instead giving a "failure to read disk" message and an instruction to hit ctrl-alt-delete to restart, which had no effect.

Since there were no audible sounds of mechanical failure, I hoped it might just be a connector problem or something, so I removed the HD and put it into an external enclosure and plugged it into a Ubuntu box (running 10.04); however, while it showed up in the filesystem as "250 GB Hard Disk: OS", attempting to navigate to it yielded only a "Unable to mount location" error with the message:

[FONT=Courier New][SIZE=1]Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware.  In the first case run chkdsk /f on Windows [...][/SIZE][/FONT]

Based on some other online discussions of this problem, I tried to run ntfsfix, but this had no effect. Are there any other things I could try? I only want to extract the data, I don't care about the disk itself.

The friend would be willing to pay for a data recovery service, so I definitely don't want to do anything that could cause problems for this. But if there's a free way I can accomplish this in Ubuntu, that would obviously be preferable....

---

