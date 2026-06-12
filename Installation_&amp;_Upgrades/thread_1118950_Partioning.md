---
title: "Partioning"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by ayyappa.konakalla on 2009-04-07
Hi all,

In my laptop Ubuntu is installed and not partioned while installing.Now i am planning to install Windows and dont want to remove Ubuntu.Can any one let me know how to go forward.

---

### Post by ronparent on 2009-04-07
Depending on the size of your laptop dive, you can use the System> Administration> Partition Editor to shrink your ubuntu partition to make room for windows either at the front or end of your drive. Windows would probably prefer being installed in front of ubuntu. How many primary partitions do you already have without windows?

Note: That installing windows on the same drive as ubuntu will rewrite the mbr requiring you to restore the grub bootloader (with the ubuntu live cd) to permit you to boot your ubuntu install.

---

### Post by upchucky on 2009-04-07
install xp after ubuntu

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

