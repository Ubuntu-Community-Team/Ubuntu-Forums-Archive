---
title: "External Hard disk Install"
date: 2013-02-08
forum: Hardware
---

### Post by gavinjb on 2013-02-08
Hi,

I am trying to configure an External Hard disk when connected to my machine to mount to a /media/BackupDrive

I have the UUID, but not sure what the best way to set it up to mount to this point is, if it was a device that would be connected on boot then I would add it to fstab, but as the device could be connected at anytime, I need Ubuntu to be able to detect and then mount it, any suggestions on how I can do this.

Thanks,



Gavin,

---

### Post by sudodus on 2013-02-08
In an Ubuntu desktop system, a USB drive will be auto-mounted when connected, which can be seen in a file browser.

If it has an entry in /etc/fstab with the option [FONT="Courier New"][SIZE="3"]noauto[/SIZE][/FONT], the system will not complain, if the drive is absent at boot. It will not be auto-mounted when connected, but you can mount it easily only specifying the device, label or mount point (according to what is specified in /etc/fstab. For example

```
sudo mount /media/BackupDrive
```
or if it has the label BackupDrive
```
sudo mount -L BackupDrive
```

However, you can't mount it with the file browser, unless you run that with gksudo, because you need superuser privileges to mount what is in /etc/fstab.

See ```
man mount
``` and ```
man fstab
```

---

### Post by gavinjb on 2013-02-09
Thanks, that did it, I remember doing something different years ago, so that when I plugged a device in it mounted it and also recognized when it was removed, but this does what I need, as I now have my backup script check to see if the device is mounted and if not try and mount it.

---

