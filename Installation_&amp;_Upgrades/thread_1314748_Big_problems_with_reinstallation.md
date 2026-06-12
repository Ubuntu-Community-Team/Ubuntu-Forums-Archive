---
title: "Big problems with reinstallation"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by KegHead on 2009-11-04
Hi!

After numerous problems with 9.10 I decided to reinstall 9.10 Via an USB.  

I'm having huge problems, is there anyway to completely remove the old 9.10?

Thanks!

KegHead

---

### Post by jjcv on 2009-11-04
> **KegHead said:**
> Hi!

After numerous problems with 9.10 I decided to reinstall 9.10 Via an USB.  

I'm having huge problems, is there anyway to completely remove the old 9.10?


You don't actually have to.  when you do the reinstall you can then go into the partition editor and chose to remove the old partitions then or get the new version to reformat the old partitions and install.  

Alternatively in the livecd you can boot.  Run fdisk /dev/sd0 (your hard drive may be different)

then type "p" to list the partitions/

type "d" to remove partitions (1 at a time)

type "w" to save the changes.

Then reboot and the partitions are gone.

---

### Post by KegHead on 2009-11-05
hi!

I'm unable to install with a pen drive.

unable to format ect.

no access to terminal.

---

### Post by KegHead on 2009-11-05
Hi!

Is there anyway to force an installation of 9.10 using a pendrive?

Nothing seems to work.

KegHead

---

