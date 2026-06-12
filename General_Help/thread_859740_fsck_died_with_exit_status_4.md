---
title: "fsck died with exit status 4?"
date: 2008-07-14
forum: General Help
---

### Post by DeanZ on 2008-07-14
So I went to boot up ubuntu which was working 6 hours ago and i got a black screen after some of the loading bar.  Some of what came up is:

/dev/mapper/computer-root:unexpected inconsistency

Run fsck manually

fsck died with exit status 4

after 2% fail

bash command line not found
several more lines not found starting with bash

378 possibilities then y/n to see what they are

I have had ubuntu installed for about 4 months without issue, it is on a separate HD which is a 1 1/2 years old and my windows hd is still fine, the computer was off the entire time I was gone, what could have happened?  What can I do?

---

### Post by ghost_ryder35 on 2008-07-14
> **rubbsdecvik said:**
> I fixed it.

Ran LiveCD 

Ran fsck with auto fixing and verbose mode.

Restarted... worked like a charm.

Hope this may help someone else out there.

[http://ubuntuforums.org/showthread.php?t=367644](http://ubuntuforums.org/showthread.php?t=367644)

---

### Post by Jim! on 2008-07-14
Hmmm.... That is strange, generally fsck occurs after a computer experiences a crash or is not shutdown properly in some form of another (power outage, forced shutdown, etc) Did you turn your computer off properly the last time you used it?

EDIT: Ah!, looks like someone found a solution before I finished posting. It looks promising, hope it fixes your problem;)

---

### Post by Taxman415a on 2008-07-14
Lots of things could have happened from a power spike to minor drive failure, etc. Yes they can happen selectively.

The important thing is you need to drop to run fsck. You can either do it from a livecd as above or in single user mode. The 'Run fsck manually' is the key letting you know you really do have to do that. Error code 4 just says it exited with uncorrected errors. See man fsck for options.

It does unfortunately look like you lost some things, they may or may not be recoverable. Hopefully you have good backups. If you haven't booted into Ubuntu yet, just choose the recovery option in Grub to get to single user mode.

---

### Post by ghost_ryder35 on 2008-07-14
> **Taxman415a said:**
> Lots of things could have happened from a power spike to minor drive failure, etc. Yes they can happen selectively.

The important thing is you need to drop to run fsck. You can either do it from a livecd as above or in single user mode. The 'Run fsck manually' is the key letting you know you really do have to do that. Error code 4 just says it exited with uncorrected errors. See man fsck for options.

**It does unfortunately look like you lost some things**, they may or may not be recoverable. Hopefully you have good backups. If you haven't booted into Ubuntu yet, just choose the recovery option in Grub to get to single user mode.
i wouldn't assume that just yet.

---

