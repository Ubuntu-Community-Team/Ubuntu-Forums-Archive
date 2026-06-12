---
title: "Command to mount other logical drivers"
date: 2008-12-02
forum: General Help
---

### Post by windhair on 2008-12-02
With the system menu, I can access other logical drivers in my PC, but what is the command to mount them from console?

---

### Post by drs305 on 2008-12-02
I was halfway through an explanation when I realized the ubuntu wiki would be more comprehensive:
[https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")

Before running the mount command, you genereally will need:
To know the device designation and file type: sudo blkid
To have a mountpoint (unless using pmount): sudo mkdir /media/xxxx
To have permissions to access, and perhaps write to the mountpoint with the chmod command.
To use 'sudo' unless the device is listed in fstab and a user option is designated.

Here is an example of a basic mount command:
sudo mount /dev/sda3 /media/mymountpoint -t ext3

You can learn a lot by reading the man page:
```

man mount

```

---

