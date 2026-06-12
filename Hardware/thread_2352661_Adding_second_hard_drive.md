---
title: "Adding second hard drive"
date: 2017-02-14
forum: Hardware
---

### Post by Autodave on 2017-02-14
Xubuntu 14.04 (because I need older version for software). I have a second HD formatted to NTFS. I need it to automatically mount on boot. I know that I need to edit the fstab file, but exactly what to I need to add/change in that file?

---

### Post by howefield on 2017-02-14
To edit the fstab file use..

```
sudo nano /etc/fstab
``` 

My ntfs disk is mounted with the following...

```
UUID=2815A7B127D66E41 /NtfsData       ntfs    defaults,umask=007,gid=46 0       0
```

add your line to the bottom of the file, then save with Ctrl + O, enter and Ctrl + X

You would obviously need to sub with your UUID and mount point. To get the UUID, use..

```
ls -al /dev/disk/by-uuid
```

Check all is well with..

```
sudo mount -a
```

I think that would do it.

---

### Post by Autodave on 2017-02-14
Thank you.  That worked. However (no fault of your's) I now have a problem related to that. I use Audacity to record on Sundays: 18 tracks via USB cable. In order to get enough HD speed, I use one HD to run the program and the second to record the music. I wanted the second HD to auto-mount on boot so that I don't always have to remember to mount it. If I don't mount it, Audacity defaults back to the first HD. Here is the wierd part:

With the second HD mounting at boot, Audacity is not seeing it! If I disable the auto-mount and mount the second HD manually, Audacity is happy. Any thoughts on that? Or do I need to make a new post about this?

---

### Post by howefield on 2017-02-15
> **Autodave said:**
> With the second HD mounting at boot, Audacity is not seeing it! If I disable the auto-mount and mount the second HD manually, Audacity is happy. Any thoughts on that? Or do I need to make a new post about this?

If other applications can see the drive then it sounds like your Audacity configuration for that particular job. If it is any deeper than that I'd suggest starting a clean new thread.

---

