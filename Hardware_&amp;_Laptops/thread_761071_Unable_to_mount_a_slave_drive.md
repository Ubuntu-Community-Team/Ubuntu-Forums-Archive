---
title: "Unable to mount a slave drive"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by SuzuZaku on 2008-04-20
I just hooked up a slave drive to my computer, but it kept giving me the error message: "Unable to mount volume".
So I tried to force mount it and it gave me the message:

> suzuzaku@Masternode:~$ sudo mount /dev/hdb1 /mnt/slave
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hdb1 /mnt/slave -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hdb1 /mnt/slave ntfs-3g defaults,force 0 0

So I have no idea what to do...
Please help me! What do I need to do?

---

### Post by Gen2ly on 2008-04-20
check the drive using fsck to look for errors

```
fsck /dev/yourdevice
```

and try to remount it.  Also too, option -t will tell mount the filesystem of the drive.

Good luck.

---

