---
title: "Automounting external USB ext4 partition to a chosen folder and permissions"
date: 2019-02-17
forum: Hardware
---

### Post by dowoshek on 2019-02-17
Hi,
I'd like to use ext4 partition on my USB HDD. I don't need it to be mounted all the time, just when I'll plug the usb cable in. So how can I configure it to automount  in /mnt/MYDISK with full permissions for every user? Currently, only root have access.

---

### Post by TheFu on 2019-02-17
If it has ext4 as the file system, this a a permissions issue and a mount issue.
Don't use a GUI to mount it.  Use either the fstab or autofs or manually run the mount command.

As for permissions, what is your skill level with those and how much do you care about security?

---

