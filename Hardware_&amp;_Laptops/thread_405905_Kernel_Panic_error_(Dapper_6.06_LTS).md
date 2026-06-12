---
title: "Kernel Panic error (Dapper 6.06 LTS)"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by pcolamar on 2007-04-10
Hi there,
  
I have done some change to my HD configuration and now I am getting a strange Kernel Panic error.
Beforehand, let me say that is strongly possible that Ubuntu was in hibernation when I did all the changes via WinXP. The changes to the HD consisted changing all but the Win XP partition from primary to logical, consequentially all the partitions have a different hdaX number.
Important to note that the old SWAP has moved from hda3 -> hda7 now.

---------- The message on the screen when booting is:

...
...
Begin. Running /scripts/local-premount.....
[17179574.9760000] Attempting manual resume
[17179574.9760000] attempt to access beyond end of device
[17179574.9760000] hda3: rw=16, want=8, limit=2
[17179574.9760000] Kernel panic - not syncing:I/O error reading memory image
[17179574.9760000] 
-------------------------------------

then the laptop hangs, no keystroke has any effect and I have to turn it off.

I have tried to locate the /scripts directory without success (maybe it's a symbolic link !).
Any suggestion ?
If, as I think, it's an attempt to resume from a Swap area not existing any longer, how can delete the resume flag and let it boot normally?

I have already changed the fstab file correcting all the /dev/hda*X* definitions
Thanks

Palmer

---

### Post by pcolamar on 2007-04-12
Bump

---

