---
title: "Would like to move from duel-boot to VM's"
date: 2008-11-02
forum: General Help
---

### Post by Monotoko on 2008-11-02
Hiya, i have recently tested running Ubuntu inside XP on a VM, and it works extreemly well, i would in fact like to move to that system, rather than my current duel-booting system.

Only thing is, im not too sure how to restore the MBR to Windows, i know that if i delete the ubuntu partition, im gonna get an error from GRUB, is there any way i can give Windows back control of booting without reinstalling it?

---

### Post by LaRoza on 2008-11-02
You can restore the Windows MBR with the Super Grub Disk. See the link in my sig.

If you are running Ubuntu and Windows, you can use the super grub disk to restore the MBR, then reboot. Windows should automatically launch, and you can safely use the Windows tools (Disk Management) to delete the Ubuntu and Swap partitions and extend the Windows partition.

---

