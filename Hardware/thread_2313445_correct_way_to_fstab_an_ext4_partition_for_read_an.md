---
title: "correct way to fstab an ext4 partition for read and write for all?"
date: 2016-02-12
forum: Hardware
---

### Post by ELD on 2016-02-12
I am wondering what the correct way to have an ext4 storage partition mounted at startup are?

I had the Ubuntu installer set it to /media/storage but it seems the default permissions the installer gives is a bit junk.

> UUID=a133052b-d144-4f79-a86d-1adda74335b1 /media/storage  ext4    defaults        0       2
That's what it gave me.

I want all users to be able to read and write into it.

Currently I can't delete to the trash, as it seems it's not setup correctly, I can only delete files.

---

### Post by yancek on 2016-02-12
The entry below works for me on the data partition.  Change device and mount point to suit your system.

> /dev/sda9 /mnt/data ext4 auto,user,rw 1 2

Permissions on the mount point as below.  The users you want to have rw access need to be in the users group or whatever group you set.

> drwxrwxr-x 18 owner users 4096 Feb  5 07:41 /mnt/data/


Sending something to the Trash is just moving it to another location on the system while deleting is deleting.  There should be an option to "Send to Trash" as well as Delete.

---

### Post by weatherman2 on 2016-02-12
> **ELD said:**
> I am wondering what the correct way to have an ext4 storage partition mounted at startup are?

I had the Ubuntu installer set it to /media/storage but it seems the default permissions the installer gives is a bit junk.


That's what it gave me.

I want all users to be able to read and write into it.

Currently I can't delete to the trash, as it seems it's not setup correctly, I can only delete files.

The fstab file is where you choose what partitions to mount and where the mountpoints are.  It isn't where you choose which users have permission to read/write to it.

I suggest not using /media for partitions you will mount yourself like this.  Leave /media for Nautilus to mount drives you plug in like USB and portable drives.  Use /mnt or somewhere place.  Create a directory under /mnt (the intended place to mount drives like this):

```
sudo mkdir /mnt/storage
```

Or just make one at the top if you wish:

```
sudo mkdir /storage
```

Then put that in your fstab:

```
UUID=a133052b-d144-4f79-a86d-1adda74335b1 /mnt/storage ext4 defaults 0 2
```

(or replace "/mnt/storage" with "/storage" if you prefer.)

Save your edited fstab file, unmount the drive if it was already mount it, then re-mount according to your fstab file:

```
sudo mount -a
```

Note that the mount command above gives NO output if everything in your fstab file was mounted correctly; if not, you get an error.

Once you've got it mounted, you can set the permissions for all users:

```
sudo chmod -R a+rwx /mnt/storage/
```

---

