---
title: "unmounted USB drive files still showing"
date: 2015-01-21
forum: Hardware
---

### Post by Constantino_Schill on 2015-01-21
hey everyone,

I've got an external RAID enclosure (USB) that I'm using as my daily backup.  Typically, I mount it at */media/external/* and then run my automated rsync scripts in order to complete my backup.

The thing that's got my scratching my head is that, when I unmount and turn off the USB drive, and do an *ls /media/external/* I can still see all the files.  What's more, I can also delete and open the files ... (one potential clue into things is that when I do a *umount /media/external/ *sometimes the system tells me that it's not mounted - strange given that I've never unmounted it)

This wasn't behavior that I was expecting.  Furthermore, I want to ensure that I haven't done anything wrong since our backups are critical to us.

As a side note, we have another RAID enclosure that we use as a weekly backup.  It is an encrypted backup (ecryptfs) and it behaves as I expected (when unmounted and powered off, an *ls *on it's mount directory reveals an empty directory)

---

### Post by Constantino_Schill on 2015-01-21
Looks like I've figured things out.

Before running the automated backup script, I wasn't checking whether the drive was actually mounted.  Therefore, I had previously run the backup into */media/external/ *without the drive actually mounting; when this happened, it created a copy of all the files within that directory and made all the files still available even if the external drive was not powered on.

In case people are wondering, here is how I'm checking if things are mounted properly in my bash script:

```
if (mount | grep '/media/external'); then
    echo "mounted!"
else
    echo "not mounted!"
fi
```

---

### Post by weatherman2 on 2015-01-21
For backups like this, I like to mount the backup drive myself and not expect Nautilus to do it.  In fact, I don't like to mount things manually in /media - I reserve that for Nautilus to mount drives there automatically.  I tend to use /mnt instead to mount drives manually (in a script).

You can tell Nautilus not to mount drives automatically (or certain drives) - can't exactly remember how.  But you can also simply unmount the drive from /media first if it is mounted, then re-mount it yourself in your own mount point (like /mnt) before doing the backup.

---

