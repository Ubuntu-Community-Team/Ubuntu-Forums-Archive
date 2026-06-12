---
title: "Uninstallation of Ubuntu from XP/Ubuntu setup"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by hexagram1000 on 2009-05-27
I had installed ubuntu alongside xp a while ago and it never worked that well because I couldn't find the right drivers to get my wireless card working. Anyway, I decided to completely delete ubuntu from the harddrive and extend the xp partition. I did so using the ubuntu live cd. I deleted everything but the xp partition and extended the xp partition to the other partitions I erased. I then popped in the windows xp recovery cd and typed in fixmbr and fixboot. However, after doing this, the screen says that there is an error in the disk and it says cntrl alt delete to restart the computer. I popped in the ubuntu live cd to check on the xp partition and it couldn't read it, citing some magic error having occurred. Does anybody know how and if this can be fixed? Thanks.

---

### Post by lemming465 on 2009-05-30
The symptoms you describe sound like the XP partition size was changed, but without resizing the NTFS file system living on the partition.  So anything trying to read the partition is seeing a confusing mixture of NTFS and ext3 data, or something.  Particularly if the beginning of the XP partition was moved, rather than the end.

If you have good notes on the previous location and can set the partition boundaries for XP back to where they were, running "chkdsk /f" against it off a recovery disk might get you back in business.  Failing that, you probably either have to reformat the disk completely and reinstall from scratch, or resort to forensic tools such as "autopsy" if you need data back from it.

If you try to resize the partition again sometime, make sure you are using a filesystem-aware tool, not a simple disk partition table editor.

---

### Post by Mark Phelps on 2009-05-31
> **hexagram1000 said:**
> Does anybody know how and if this can be fixed? Thanks.

Lemming is right in that, your partition scheme is probably hosed now.

The GParted version bundled with Ubuntu is quite old, so you could try downloading and burning a GParted LiveCD from distrowatch and see if that is able to read the partitions.  

If that doesn't work, apart from complete reinstallation, you need to see if you can lay your hands on a copy of Acronis Disk Director or a Paragon Disk Manager product.  When dealing with MS Windows partitions, it's really best to use Windows products, not GParted.

---

