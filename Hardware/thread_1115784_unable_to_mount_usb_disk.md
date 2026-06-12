---
title: "unable to mount usb disk"
date: 2009-04-04
forum: Hardware
---

### Post by arvsr1988 on 2009-04-04
i changed the mount volume settings for my usb disk on my computer and ever since its not mounting on my pc.  the following errors are displayed when the USB disk is plugged in:

Error 1:
unable to mount 8.0GB media

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Error 2:
Cannot mount volume
unable to mount volume
(details)mount point cannot contain the following characters: newline G_DIR_SEPERATOR (usually /)

please tell me how to fix this asap. thanks.

---

### Post by utnubuuser on 2009-04-04
Have you tried plugging the USB device into a Windows machine, then "unmounting safely"?

---

### Post by arvsr1988 on 2009-04-05
i used the command  sudo u mount -t vfat /dev/sdb1 /media/disk -o user,uid=1000,gid=1000 after creating a folder called disk in desktop and moving it to /media/. the usb mounted... after that i went to the options and removed the mountpoint i set. upon removing and plugging in, the automount started working...

---

