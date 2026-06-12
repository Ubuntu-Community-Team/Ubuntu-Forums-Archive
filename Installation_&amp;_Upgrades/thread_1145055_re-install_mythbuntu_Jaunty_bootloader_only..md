---
title: "re-install mythbuntu Jaunty bootloader only."
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by bergqvistjl on 2009-05-01
hi, im reinstalling windows, which means it will overwrite my current GRUB bootloader. is there anyway to restore the grub bootloader without re-installing the whole distro again? the partitions will be the same as before, same layout/size etc. and i have the current bootloader settings stored in etc/grub.lst or whereever its stored. so, is there any way to resore the bootloader?
EDIT: im using the default mythbuntu 8.10 (i upgraded to jaunty) partition layout, whether the upgrade changed the partitions or not, i dont know. Also, the windows partition is 1 NTFS partition.

---

### Post by mikechant on 2009-05-01
Think I can do this from memory now!

1/ Boot live CD
2/ Open a terminal and enter the following command
sudo grub
and you should get a prompt - grub>

3/ Enter the following command at the grub prompt
find /boot/grub/stage1

3/ This should return '(hdx,y)' where x and y are the disc and partition numbers, e.g. (hd0,4)

6/ now enter these commands at the grub prompt
root (hdx,y)
setup (hdx)
exit

(substituting your x and y values)

Now you should be able to boot.

If the find command finds nothing or gives multiple results stop at that point and let us know.

---

### Post by bergqvistjl on 2009-05-01
ok thanks.

---

