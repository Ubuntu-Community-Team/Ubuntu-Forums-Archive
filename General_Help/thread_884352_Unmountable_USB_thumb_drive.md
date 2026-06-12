---
title: "Unmountable USB thumb drive"
date: 2008-08-08
forum: General Help
---

### Post by Virgofenix on 2008-08-08
I improperly removed my USB thumb drive from a Windows machine (just pulling it out without the 'Safely remove device' ritual), so, now, I can't mount it on my Ubuntu machine. Is there any way of mounting it on my Ubuntu machine without having to use Windows? Not that I don't have any access to a Windows machine. It's just that a lot of people don't bother removing USB thumb drives from Windows properly; and I don't want a fun, fun Linux session being forced to end because I have to reboot into Windows just to mount a USB drive - that's just lame.

---

### Post by cdtech on 2008-08-08
Run 'ntfsfix' on the USB device within Linux, which will reset the NTFS journal.

---

### Post by falcon61102 on 2008-08-08
Besides running ntfsfix, you can also manually mount the drive using the force option "-f".  That will also reset the NTFS journal and mount the drive for you.  Both options work well.

---

