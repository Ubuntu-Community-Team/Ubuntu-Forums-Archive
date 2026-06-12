---
title: "Mounting a second drive (ext4) in ubuntu, missing something"
date: 2009-05-01
forum: Hardware
---

### Post by shamusl on 2009-05-01
Installed a new drive today, and opened gparted and formatted for ext4 for the whole device, I don't really understand how to mount it, because when I type in the command, I get a "can't find /dev/sdb1 in /etc/fstab or /etc/mtab" error. What am I doing wrong?

---

### Post by drs305 on 2009-05-01
The basics, assuming you are running an ext4 system:

Make a mount point:
```
sudo mkdir /mnt/mountpoint  # Pick the name for "mountpoint" and use it throughout
sudo chown -R *yourusername:* /mnt/mountpoint  # Example: sudo chown -R john: /mnt/mountpoint

```

Find the UUID of your new drive:
```
sudo blkid | grep "sdb1"  # assuming it's sdb1
```

Backup fstab and open for editing:
```

sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```

Add the entry to fstab:
```

UUID=XXXXX-XXXXX-XXX /mnt/mountpoint ext4  defaults 0 2

```
Save and run the mount command:
```

sudo mount /dev/sdb1

```
If you see nothing, it means it was mounted without errors. If you get errors, report them here.

---

### Post by shamusl on 2009-05-01
Mounted volume as storage, however I have no idea how to access the device, gparted says the device is mounted though, which is good. The device is mounted, but how do I access it?

---

### Post by drs305 on 2009-05-01
> **shamusl said:**
> Mounted volume as storage, however I have no idea how to access the device, gparted says the device is mounted though, which is good. The device is mounted, but how do I access it?

Open up your file browser. It's in /mnt/storage. You can drag a shortcut onto the Desktop or into the bottom section of Places (nautilus).

You could also repeat the process above and change the mount point to /media/storage if you prefer. The /media folder has traditionally been for removable devices. Devices mounted in /media will appear on your Desktop (if it's turned on) and in Places, without you having to make shortcuts.

---

### Post by shamusl on 2009-05-01
> **drs305 said:**
> Open up your file browser. It's in /mnt/storage. You can drag a shortcut onto the Desktop or into the bottom section of Places (nautilus).

You could also repeat the process above and change the mount point to /media/storage if you prefer. The /media folder has traditionally been for removable devices. Devices mounted in /media will appear on your Desktop (if it's turned on) and in Places, without you having to make shortcuts.

Thanks, but now I'm having another problem, sorry. I don't have permission of the folder /mnt/storage, how do I change it from root to me?

---

### Post by drs305 on 2009-05-01
> **shamusl said:**
> Thanks, but now I'm having another problem, sorry. I don't have permission of the folder /mnt/storage, how do I change it from root to me?

That should be the second command in post #2:
```
sudo chown -R *shamusl*: /mnt/stoarge  # Example: sudo chown -R john: /mnt/mountpoint
```

Make sure you substitute your actual *username* and have the correct mount point (/media/storage, /mnt/storage, or whatever it is).

---

