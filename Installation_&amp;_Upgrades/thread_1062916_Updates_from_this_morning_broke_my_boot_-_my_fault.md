---
title: "Updates from this morning broke my boot - my fault though"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by knipknup on 2009-02-07
During some automatic updates this morning, a window popped up notifying me that a file was going to be changed to the 'installers' version.  This gave me several options to select from.  One was to install the new version, another to leave with my current, another was to merge, there were also options to display side by side, etc.  I viewed the file changes that would be made and it basically added (hd0,0) to my existing (hd0,1).  I make a bad choice :( and selected merge.  Once I did the reboot, I received the bootloader error that volume could not be booted.
I can boot into windows and I can access the linux files using 'DiskInternals Linux Reader'.
Can someone direct me to what file houses the bootloader instructions?  I can easily remove the (hd0,0) references but am batting zero on finding that pesky file.

Thanks.

---

### Post by taurus on 2009-02-07
It's the /boot/grub/menu.lst.

---

### Post by knipknup on 2009-02-07
Excellent, I found it and will get it fixed.

---

