---
title: "Whole partition backup of an external hard drive"
date: 2009-07-13
forum: Hardware
---

### Post by Ru$$i@N on 2009-07-13
Hello,

I just got a Hammer Storage 1TB external hard drive. I intend to store large files on the thing, but the default partition on it is FAT32, so I'm going to partition it to ext3.

I would like to make a backup of the original partition (FAT32), and obviously all of the files that come with the drive, in case i need to get it back to the original setup.

I've just tried partimage, the setting up part couldn't be easier, but the problem is that the copying process stops at 99% with no further progress.
It's a 1TB drive, but there's only 230+MB of storage used, which the partimage is supposed to backup, so i don't see a problem, but apparently there is one :)

Help meeeee, please.

Thanks

---

### Post by Dysport on 2009-07-13
Why don't you just tar everything on the drive into a file on your local hdd?

```

tar cvpzf backup.tgz /media/"path-to-your-external-drive"
```

Then you have a backup of your external harddrive in your home directory.

---

### Post by Ru$$i@N on 2009-07-13
> **Dysport said:**
> Why don't you just tar everything on the drive into a file on your local hdd?

```

tar cvpzf backup.tgz /media/"path-to-your-external-drive"
```

Then you have a backup of your external harddrive in your home directory.

yeah, i ended up doing that. For some reason partimage doesn't work for me.

---

