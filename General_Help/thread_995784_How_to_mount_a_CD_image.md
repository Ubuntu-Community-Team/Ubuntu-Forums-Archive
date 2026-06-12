---
title: "How to mount a CD image"
date: 2008-11-28
forum: General Help
---

### Post by trendyabinash on 2008-11-28
I want to mount a CD image and I don't know how to do that in linux as I am new to UBUNTU and Linux.

In windows I used daemon tools, do we have any software like that for linux?

Please guide me.
thanks in advance

---

### Post by marshall.robert on 2008-11-28
Applications -> Add/Remove... search for gmount, the results should sort you out.

---

### Post by albandy on 2008-11-28
from command line:
sudo mount /path_to_iso_file/file.iso /destination_folder -o loop -t iso9660

For example:

sudo mount /home/user1/backup.iso /mnt -o loop -t iso9660

---

### Post by drs305 on 2008-11-28
This command should mount the iso. You can use any mountpoint that currently exists:
```

sudo mount -o loop /path.to.iso/filename.iso  */media/yourmountpoint*
```

In Intrepid, there is an option to right click on an iso file in nautilus, select 'Open with' and Archive Manager but I have had mixed results with this method.

---

### Post by trendyabinash on 2008-11-28
thanks guys

but gmount all other suggestion only supports ISO format, what about others???
like .nrg .daa .mds and types

---

### Post by drs305 on 2008-11-28
> **trendyabinash said:**
> thanks guys

but gmount all other suggestion only supports ISO format, what about others???
like .nrg .daa .mds and types

In the mount command I gave you omitted the "-t" option because I believe .iso is handled by default. The mount command supports lots of formats although I don't see the ones you specifically mention. For these you might try to add the "-t *fstype*' switch.

You can see the multitude of file systems supported by *mount* by looking at the *man* page and the *-t* switch.
```
man mount
```

---

### Post by albandy on 2008-11-28
Try this:
[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

---

### Post by slmouradian on 2008-11-28
Applications -> Add/Remove

Search for MountManager.

That might be useful.

---

### Post by trendyabinash on 2008-11-29
ok thanks
I will give it a try

---

