---
title: "Help with a Grub entry? Boot from a memory stick"
date: 2009-11-12
forum: Hardware
---

### Post by Gogeden on 2009-11-12
Is there a way I can edit the Grub Menu so I can make grub list Damn Small Linux and then have it proceed to boot DSL from a memory stick (NOT Flashrdive). Where do I begin? I'm stuck on the "root to" entry.


# This entry links to the DSL installation on my 2GB Memory stick
title        Damn Small Linux
root        (hd1,0)
kernel        /boot/isolinux/minirt24.gz    root=/media/FD86-21EC
initrd        /KNOPPIX/KNOPPIX.sh
savedefault
boot


That's the exact entry. Please help thanks :lolflag:

---

