---
title: "dual boot problems"
date: 2011-05-19
forum: Hardware
---

### Post by linux_trojan on 2011-05-19
I bought a Dell XPS with Ubuntu already installed.  I created a NTFS partition and tried to install Windows for dual boot.  However, when I try to install windows, it says no windows partition found.  I have totally repartitioned and still no luck.  This happens with Vista and XP CDs.  I am having a similar problem on my Dell desktop.  Did Dell put something in the hardware to block linux distros?  Perhaps I need to reformat the MBR too?  I have no idea what the problem is, this is very strange.

---

### Post by oldfred on 2011-05-19
Did you make the NTFS partition a primary partition and put the boot flag on that NTFS partition. Windows only boots from, repairs, and installs to primary partitions with boot flag. Second installs can be in a logical partition but all boot files are literally moved to the primary. It will also install to free space if a primary partition is available as it will then create a primary partition with the boot flag.

---

### Post by linux_trojan on 2011-05-19
No, dont think I did all that.  I will give it another shot.  Thanks

---

