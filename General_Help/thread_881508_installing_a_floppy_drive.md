---
title: "installing a floppy drive"
date: 2008-08-06
forum: General Help
---

### Post by krysia on 2008-08-06
iI have ubuntu 8.04 installed on my pc and I have added an old floppy drive from a previous pc.the problem is it turns on when you put a floppy in then shutys down. t6he floppy in the drive doesnt show up,when I go to my computer it shows the floppy drive but when I click on it a box appears and says cant mount the volume.
help please.
krysia

---

### Post by geirha on 2008-08-06
Could you post the content of /etc/fstab? 

Also, try mounting it manually as root and see if that works. These commands run from a terminal should work.
```

sudo mkdir /media/floppy          # creates a mount point in case it doesn't exist
sudo mount /dev/fd0 /media/floppy # the actual mount

sudo ls /media/floppy             # list content of floppy
sudo umount /media/floppy         # unmount it

```

If you added the floppy-drive after you installed ubuntu, then you probably just lack a line for it in fstab. Adding a line like this to /etc/fstab might just do the trick if mounting it manually worked:

```

/dev/fd0        /media/floppy auto      user,noauto     0       0

```

---

### Post by krysia on 2008-08-06
thanks for your help it seems what I wasdoing wasputting a blank floppy in the drive,once I put in a floppy with data it worked.
sorry for being thick.
krysia

---

