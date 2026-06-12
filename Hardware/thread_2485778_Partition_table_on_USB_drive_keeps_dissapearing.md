---
title: "Partition table on USB drive keeps dissapearing"
date: 2023-04-09
forum: Hardware
---

### Post by kabirgandhiok on 2023-04-09
Hi,

I've been trying to format and create Windows compatible partition table on a USB stick but every time I eject the drive after creating the partition, it gets deleted or disappears.

I have tried the disks gui to do this and by the terminal using the following:
```

sudo dd bs=1M if=/dev/zero of=/dev/sdb && sync
sudo fdisk /dev/sdb
sudo mkfs.vfat -F 32 /dev/sdb1

```
Running
```
lsblk
``` 
shows partition as 
```
/dev/sdb1
```

I can then copy files into it. But as soon as I eject it and connect it again on the same system everything gets deleted and the partition isn't visible anymore.
Running
```
lsblk
``` 
after ejecting and connecting again shows 
```
/dev/sdb
``` 
with the partition table missing.

Can anyone help me understand why this is happening?
Thanks for taking the time.

---

### Post by sudodus on 2023-04-09
The behaviour you describe is typical for a 'read-only' drive. The drive 'accepts' commands that create a file system, but even after flushing the buffers alias 'safe removal' alias ejecting (in a terminal window with the command **[FONT=Courier New]sync[/FONT]**) nothing remains after unplugging and replugging or after reboot.

You can analyze the problem according to [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035) and if you are lucky, find a solution.

---

