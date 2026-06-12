---
title: "[SOLVED] Cant Mount Volume??"
date: 2008-11-20
forum: General Help
---

### Post by Kaneda187 on 2008-11-20
I cant go into my windows partition all it says is invalid mount point option......any ideas? its really bugging me!

---

### Post by taurus on 2008-11-20
Do you know your windows partition?  Assuming it's /dev/sda1, try to run these commands from a terminal to see if you can mount it.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows
```

---

### Post by Kaneda187 on 2008-11-20
okay thanks i think that would have worked if i didnt try to fix it in the mean time by install mount manager now i cant even find it....:( HELP!! please

---

### Post by drs305 on 2008-11-20
Run and post the following command. It will show us the partitions on your system. The windows partition will be the one (or one of) with "NTFS" as the type.

```
sudo blkid
```

You might also run the following in case your other app actually did mount it:
```
mount
```

---

### Post by taurus on 2008-11-20
Post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by Kaneda187 on 2008-11-20
Okay i have it mounted again now how can i set it mount on start up? thanks for the help guys!

---

### Post by drs305 on 2008-11-20
> **Kaneda187 said:**
> Okay i have it mounted again now how can i set it mount on start up? thanks for the help guys!

Assuming you are still talking about your windows ntfs partition:
```

mkdir /media/windows
sudo chown *yourusername:* -R /media/windows
chmod 750 -R /media/windows

```

Backup and edit fstab:
```
cp /etc/fstab /etc/fstab/backup
gksudo gedit /etc/fstab
```

Change the /dev/sda1 address to the real address for your windows partition. Run either "sudo blkid" or "sudo fdisk -l" to determine the actual windows partition - it may not be /dev/sda1. Add the line to fstab:
```

/dev/**sda1** /media/windows ntfs-3g auto,users,uid=1000,utf8,umask=027 0 0

```
Save and exit.

Mount:
```
sudo mount -a
```

---

### Post by Kaneda187 on 2008-11-20
Thanks a mill dude:)

---

