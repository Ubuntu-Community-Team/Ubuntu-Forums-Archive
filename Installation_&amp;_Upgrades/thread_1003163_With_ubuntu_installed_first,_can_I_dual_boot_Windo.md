---
title: "With ubuntu installed first, can I dual boot Windows XP?"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by JohnParker on 2008-12-05
Ive tried this many times, but the guide on Apcmag doesn't Work, is there a good guide on the forums? I can't seem to find one. Ubuntu 8.04

---

### Post by Partyboi2 on 2008-12-05
Boot a ubuntu live cd and use gparted (System>Admin>Partition Editor) and resize your existing ubuntu partition down to the size you want it, then with the newly unallocated space create a ntfs partition for windows. Then boot the windows cd and install to the newly created ntfs partition. Once windows is installed reboot the ubuntu live cd and use [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") to restore grub as windows would have written to the mbr.

Edit: At what stage does the apcmag guide not work?

---

### Post by JohnParker on 2008-12-06
The APC guide fails at....Windows wanting to install on the partition. It just epic fails. It wants to reformat the entire drive.

---

### Post by Partyboi2 on 2008-12-07
Does it want to reformat the whole drive or just the partition that you are wanting to install windows to? When you choose where you want to install windows to it will then ask you how you want that partition formated and give you a list of options. See screenshot and let me know if this is what you are getting.

---

### Post by euchrid33 on 2009-01-27
This worked just fine for me, except that once I rebooted and reinstalled GRUB, the XP does not appear.  By default my system boots into Ubuntu, and I have to hit ESC on startup just to see the menu.  When I do, it just lists Ubuntu twice.

Any advice?

---

