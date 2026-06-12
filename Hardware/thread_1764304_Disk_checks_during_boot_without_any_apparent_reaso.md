---
title: "Disk checks during boot without any apparent reason"
date: 2011-05-21
forum: Hardware
---

### Post by stefanofalone on 2011-05-21
Hi everyone,
I've been an Ubuntu 10.04 64 bit user for one year. My Ubuntu distro is installed on an ext2 file system. 
Occasionally, I experience disk checks during boot without any system freeze or power loss.
Sometimes, once reboot, the system works fine but Evolution Mail requests a new account, as if it was used for the very first time.
Does anyone know how to fix this problem?
Thanks a lot for help in advance.

Stefano

---

### Post by sanderd17 on 2011-05-21
I don't know about the evolution problem, but the filesystem checks are normal. fsck happens at each x startups.

---

### Post by prshah on 2011-05-21
> **stefanofalone said:**
> My Ubuntu distro is installed on an ext2 file system. 

ext2 is a non-journalling file system, and the symptoms you are describing point to corrupt files (look in /lost+found).

Please switch to ext3, or preferably, ext4.

If you are, in fact, on ext3/4, then you possibly have bad sectors, use the badblocks program (or fsck -c) to check.

Please post back if you need more information.

---

