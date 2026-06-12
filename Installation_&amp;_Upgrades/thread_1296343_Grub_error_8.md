---
title: "Grub error 8"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by coolio1 on 2009-10-20
Im a newbie with ubuntu. Its on my dell mini and I don't believe I have a disc anywhere as I dont have a disc drive. It seems everytime I turn it on I have a lot of updates to run. The last lot took an hour and now I have come to turn it on and am getting a grub prompt. I typed in boot and get 'Error 8: Kernel must be loaded before booting'
 
Any ideas please?

---

### Post by dstew on 2009-10-20
If you have a grub prompt, and want to boot a system, you have to enter **root**, **kernel** and **initrd** commands before you enter **boot**.

If you used to boot using a menu, you can use the command **configfile** to access the menu.lst file, if it exists. If your Linux partition is (hd0,0) the command might be```
configfile (hd0,0)/boot/grub/menu.lst
```
Probably one of your updates failed to create a proper menu.lst file. You might have to create one yourself.

---

