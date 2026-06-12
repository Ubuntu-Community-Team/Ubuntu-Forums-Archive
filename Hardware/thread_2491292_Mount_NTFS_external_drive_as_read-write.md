---
title: "Mount NTFS external drive as read-write"
date: 2023-10-03
forum: Hardware
---

### Post by Nickolai_Leschov on 2023-10-03
**How can I mount an NTFS external USB drive as read-write on Ubuntu 22.04 LTS?**

When I connect the drive, it is mounted automatically as read-only. By running df -h, I figured that the drive is mounted as /dev/sdb1.

When I try to mount it with
```
sudo ntfs-3g /dev/sdb1 /media/user/BRB
```

It says:

Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

I unmount it with
```
sudo umount /dev/sdb1
```

(it doesn't say anything; apparently it's fine)

Then when I try to mount it back with
```
sudo mount /dev/sdb /media/user/BRB
```

it says:

mount: /media/user/BRB: mount point does not exist.

---

### Post by SeijiSensei on 2023-10-03
To specify that the NTFS partition should have read and write permissions (in case your system is mounting with read only by default), you can use this command.

```
$ sudo mount -o rw -t ntfs /dev/sdb1 /mnt/ntfs
```

[https://linuxconfig.org/how-to-mount-partition-with-ntfs-file-system-and-read-write-access](https://linuxconfig.org/how-to-mount-partition-with-ntfs-file-system-and-read-write-access)

---

### Post by oldfred on 2023-10-03
Or did you use the NTFS with Windows and left it in the hibernated mode?
If Fast Start up on in Windows that checks the hibernation flag on all NTFS partitions. If you force write using Linux NTFS driver, you just lose that data when the hibernation is restored by Windows.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

