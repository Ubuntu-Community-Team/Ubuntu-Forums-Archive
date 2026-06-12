---
title: "How do I get an external drive auto mounted at startup?"
date: 2008-11-22
forum: General Help
---

### Post by kdfox on 2008-11-22
I have kubuntu/intrepid dual booted w/ xp.  I have an external drive (ext2) that contains all my media.  How do I get this external drive automatically mounted at startup so that I don't have to select a new wallpaper every time I login?

thanks in advance!
kdf

---

### Post by kdfox on 2008-11-23
any thoughts?

---

### Post by drs305 on 2008-11-23
You can add it to fstab:
Make the mount point where you want it mounted and make yourself the owner:
```

sudo mkdir /media/yourmountpoint
sudo chown -R *username*: /media/*yourmountpoint*
chmod -R 750 /media/*yourmountpoint*

```

Make a backup of fstab and add an entry for the partition:
```

sudo cp /etc/fstab /etc/fstab.bak
kdesudo kate /etc/fstab

```

Add this line, substituting the device name for "sdXX" and save the result. If you don't know the device name, run "sudo fdisk -l" and if you still don't know, post the results:
```

# Entry for /dev/sdXX
/dev/sdXX  /media/yourmountpoint ext2  defaults,users 0 2

```
Save the file.

Mount the partition:
```

sudo mount -a

```

For more information about fstab:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

