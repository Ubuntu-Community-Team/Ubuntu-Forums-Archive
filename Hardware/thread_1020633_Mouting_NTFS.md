---
title: "Mouting NTFS"
date: 2008-12-24
forum: Hardware
---

### Post by Paris Heng on 2008-12-24
How to mount a NTFS into Ubuntu? I want to have full access (Read/Write) to the NTFS.

The following are the screen capture of my problem:-

[IMG]http://img354.imageshack.us/img354/1498/screenshotgn8.png[/IMG]

---

### Post by taurus on 2008-12-24
Did you shut windows down cleanly the last time you used it?

---

### Post by Paris Heng on 2008-12-24
Ya, i did not shutdown cleanly. Anyway thanks for reply, problem solved.

You can auto mount the HD like this:-

> sudo fdisk -l
sudo mkdir /media/WindowsNTFS
sudo nano /etc/fstab
/dev/sda[COLOR="Blue"]x[/COLOR] /mnt/WindowsNTFS ntfs-3g quiet,defaults,umask=000 0 0

After that, restart your system.

---

