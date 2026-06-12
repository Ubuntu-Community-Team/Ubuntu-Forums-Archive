---
title: "Removable Audio Player : safe to disconnect ?"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by bleucanard on 2006-03-23
I have an iAudio M3 with a 60Gb disk. It is properly detected by ubuntu, and I can play files. The disk is FAT32. 
I have a question about disconnecting it: 
- If I select "dismount" from the context menu on the icon in the desktop,
it says it fails to unmount. It works if I "sudo umount /dev/sdb1" from the terminal. Any way to allow the desktop icon to unmount ?

- After it's dismounted, is it safe to disconnect the player ? Under Window$, if I select "disconnect device", the remote on the player eventually says "Safe to disconnect". Under ubuntu, after dismount, the remote screen on the player still says "Do not disconnect the device". I'm a bit worried that it screws up the FAT table on the disk if I just pull it out. Is it safe to just pull disconnect the device ?

---

### Post by pitr on 2006-03-23
I would say that it is totally safe to remove the device once it has been unmounted.

---

