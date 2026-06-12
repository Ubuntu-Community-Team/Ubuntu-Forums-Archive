---
title: "how to remove 8.04 from winxp, 8.04 and 8.10"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by ursahoribl on 2009-02-15
Installing intrepid on a dual boot with winxp and hardy resulted in a multiboot setup with all three systems. How do I remove hardy and free that space while retaining dual boot winxp and intrepid?

Have been using ubuntu for a couple years but am definitely out of my comfort zone and know how on this one.

grizzly

HP Pavilion dv5-1002us with AMD Turion X2 Ultra 64

---

### Post by x33a on 2009-02-15
you can boot into intrepid, then delete hardy. after that comment out the hardy entries from grub.

---

### Post by ursahoribl on 2009-02-21
x33a - your answer appeared to be too simple. When I attempted to delete hardy, received a message stating that I didn't have permissions/authorizations to perform the deletion. After a bit more research, I used parted to delete the hardy partition, started the computer with a ubuntu live CD, then did the following:

   went to a terminal
   entered the command "sudo grub"
   at the grub prompt, entered "find /boot/grub/stage1"
   wrote down the location returned by the previous command
   entered the command "root (hd0,*) where the asterisk represents the partition returned by the find command
   entered the command "setup (hd0)"
   edited /boot/grub/menu.lst tp remove the hardy entries and modify the intrepid entries to reflect the correct partition
   rebooted the computer and all was well.

Hardy was gone and the space reclaimed. Thanks for the assist, you got me thinking along the right track.

grizzly

---

