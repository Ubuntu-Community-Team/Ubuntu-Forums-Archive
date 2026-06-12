---
title: "Dual boot system w/XP Pro"
date: 2008-08-02
forum: General Help
---

### Post by dnitious on 2008-08-02
I want to run a dual boot sys w/XP Pro.  I'm curious if I need to have XP installed first and then install Ubuntu or if its better to install Ubuntu first.  Or maybe it really doesn't matter.  Please let me know, I'm new to this and don't really understand if installing one before the other makes much a difference.

PEACE!!!

---

### Post by Rocket2DMn on 2008-08-02
In general it is better to install Windows first, then GRUB will take over the MBR when you install Ubuntu, which is what you want.  If you install Windows second, it will take over the MBR, then you have to reinstall GRUB to use the dual boot.
I suggest partitioning the drive ahead of time so you don't have to resize your windows partition when you install Ubuntu.

---

### Post by dnitious on 2008-08-02
Ok.  That solves that.  Will the dual boot sys work if I want to have a raid 0 array on both OS?  If so, how do I do that.?

---

### Post by Rocket2DMn on 2008-08-02
I would think so, but I am not entirely sure.  Somebody may come by with a solid answer to that question, but if you're feeling a little adventurous, you can go ahead and try (since it doesn't sound like you have anything on it at the moment).  You may need to alternate install cd to install Ubuntu on the RAID array (not the LiveCD) - I know it was the case that you needed the alternate disc to install on RAID, though I don't know if that is still true.
Sorry for not having an entirely clear answer on this one.

---

### Post by cybrsaylr on 2008-08-03
It should work since raid 0 is a separate setting from the OSs.

---

