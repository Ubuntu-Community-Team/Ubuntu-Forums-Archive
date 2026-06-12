---
title: "Harddrive timeouts after power failure"
date: 2018-03-13
forum: Hardware
---

### Post by RichTheCoder on 2018-03-13
Would u replace the hard drive in this situation?

- We had a power failure
- my dual-boot machine booted into Windows
- so I did a few reboots to install Win updates. No problems (well, the usual incredible slowness of Win10).
- then Ubuntu wouldnt boot - "Welcome to Emergency mode ....."
- retried many times
- couldn't get in recovery mode either
- booted a LiveCD 
- mounted the real / partition and the real /home partition , and edited files there
- messed around with the network timeout and checked out the fstab 
- rebooted LiveCD 
- did fsck from the command line for the partition that mounts as /  . No errors
- did fsck from the command line on the partition that mounts as /home  . No errors 
- retried , same problem
- retried, problem went away! 
- did a  journalctl -xb  and the problem showed up as:
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
Mar 13 16:18:20 rich-OptiPlex-755 kernel: floppy0: no floppy controllers found
Mar 13 16:18:22 rich-OptiPlex-755 systemd[1]: dev-disk-by\x2duuid-d381bb29\x2d4376\x2d4c46\x2dab65\x2dbf922f3be7a9.device: Job dev-di
Mar 13 16:18:22 rich-OptiPlex-755 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-d381bb29\x2d4376\x2d4c46\x2dab65\x2dbf
-- Subject: Unit dev-disk-by\x2duuid-d381bb29\x2d4376\x2d4c46\x2dab65\x2dbf922f3be7a9.device has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit dev-disk-by\x2duuid-d381bb29\x2d4376\x2d4c46\x2dab65\x2dbf922f3be7a9.device has failed.
-- 
-- The result is timeout.
Mar 13 16:18:22 rich-OptiPlex-755 systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/d381bb29-4376-4c46-ab65-bf
-- Subject: Unit [email]systemd-fsck@dev-disk-by\x2duuid-d381bb29\x2d4376\x2d4c46\x2dab65\x2dbf922f3be7a9.servic[/email]e has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit [email]systemd-fsck@dev-disk-by\x2duuid-d381bb29\x2d4376\x2d4c46\x2dab65\x2dbf922f3be7a9.servic[/email]e has failed.
-- 
-- The result is dependency.
Mar 13 16:18:22 rich-OptiPlex-755 systemd[1]: Dependency failed for /home.
-- Subject: Unit home.mount has failed
--------------------------------------------------------------------------------------------------------------------------------------------------------------------

So it was timing out, trying to mount /home . Then, it didn't time out and it worked fine.   

Do I need a new hard drive? Anything else I should suspect?
[FONT=Verdana]
[/FONT]

---

### Post by RichTheCoder on 2018-03-23
There were two other odd symptoms : my USB ports no longer could charge my iPhone, and, booting with the "upstart" option (in the GRUB advanced-options submenu) worked successfully, while the default Ubuntu boot (with init) did not. 

The unexpected solution to both: I vacuumed the dust out of the PC's case! There definitely was a dustball touching pins in an unused MB plug.

---

