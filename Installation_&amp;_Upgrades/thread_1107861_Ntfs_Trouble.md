---
title: "Ntfs Trouble"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by uttaran on 2009-03-27
I've a 160GB hard disk.two of its partitions r ntfs.Using NTFS Configuration Tool i could auto-mount both the drives during start-up.But recently, i have resized one of those partitions in XP and I've added another 40 GB hard disk.As a result, the grub disappeared. when i restored it(without formatting), the tool doesn't auto-mount the resized drive and the new hard disk.Partition manager says both drives r ok. How to auto-mount those drives at start-up?
Also tell me how to assign a hotkey to access to system monitor.In Xp i use ctrl+alt+del to access task manager.
the error is,"AN ERROR OCCURRED WHILE TRYING TO CONFIGURE /MEDIA/SDB5"

---

### Post by Anthon on 2009-03-27
You will need to make some entries in the file /etc/fstab looking like:
/dev/sda2 /media/D  ntfs  ro,auto,users,gid=users,umask=0002,nls=iso8859-1 0 0

(make /media/D first and adapt /dev/sda2 to your system)
You can try that without rebooting using:
  mount -a
and check with 
  mount

---

### Post by Mark Phelps on 2009-03-27
If you're going to mount NTFS partitions read/write, would be better to use the ntfs-3g package.  That's available in the repos through synaptic.  Then, when you add lines to fstab, the filesystem type is ntfs-3g, not ntfs.

---

