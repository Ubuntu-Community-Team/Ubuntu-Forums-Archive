---
title: "My partition auto-mounts, but I cannot save files to it"
date: 2008-08-14
forum: General Help
---

### Post by phil81uk on 2008-08-14
I read a tutorial to auto mount my FAT32 partition, and added the following line to fstab:

/dev/sda3 /media/disk vfat defaults,nosuid,nodev 0 0

It seems that I can read files on the partition, but not save anything to it, or delete anything from it.

When I used to mount it manually (by going to Places and clicking on the disk) then it worked ok.

---

### Post by Technophobia on 2008-08-14
Who owns the folder /meida/disk ?

ls -l /media/disk

If its root than change it.

sudo chown [YOUR USERNAME] /media/disk

You may also need to change the rwx status.

sudo chmod 700 /media/disk

This will give only the owner access to read, write, and execute abilities.

Thats how I do it.

---

### Post by drs305 on 2008-08-14
Permissions are set on vfat/ntfs partitions on mounting. The easiest way to change things since you already have an fstab entry would be to change the settings to:
```

/dev/sda3 /media/disk vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137

```

Edit and save fstab, then run:
```

sudo umount /dev/sda3
sudo mount /dev/sda3

```

Note there is a tutorial in my signature line which includes '3 Minute Guide to Fstab' but just amending your fstab as above should do the job.

---

