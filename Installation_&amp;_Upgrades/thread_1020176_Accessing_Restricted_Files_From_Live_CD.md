---
title: "Accessing Restricted Files From Live CD"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by ezacharyk on 2008-12-23
I am trying to back up my files after I badly screwed my current install up. I don't really care about fixing the problem at the moment, I just want to start fresh.

The only problem is I didn't back up my files before I messed up. I also let Ubuntu create the file system last time I installed. I won't do that again.

So here I am on my laptop running an Ubuntu 8.10 live cd. I can find my existing file system in media/disk-1/

I can back up some files, but many files are restricted and I cannot access them. This includes my Firefox and Thunderbird profiles, my bittorrent downloads and my ISOs etc.

How do I access these files in order to back my stuff up before performing a fresh install.

---

### Post by taurus on 2008-12-23
Run nautilus with root privilege.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by albinootje on 2008-12-23
> **ezacharyk said:**
> So here I am on my laptop running an Ubuntu 8.10 live cd. I can find my existing file system in media/disk-1/

I can back up some files, but many files are restricted and I cannot access them. This includes my Firefox and Thunderbird profiles, my bittorrent downloads and my ISOs etc.

How do I access these files in order to back my stuff up before performing a fresh install.

You would use sudo from within the live cd session in order to access those files on your hard disk.

Are you planning to backup to DVD or usb-disk or over the network ?

If you're using some usb-disk with FAT32 file-system it makes sense to use an archive application to make the backup otherwise permissions will be messed up (all executable..).

For example, assuming that your usb-disk is at /media/disk-2 :
```

sudo tar czvf /media/disk-2/homedir.tgz /media/disk-1/home

```
If you prefer to use a gui, you can use nautilus with the "create archive" right mouse click option, like this :
```

gksu nautilus

```
Make sure you move the resulting file to your usb-disk.

---

### Post by ezacharyk on 2008-12-23
Thanks guys. That took care of it.

I'm all backed up now and ready to go.

---

