---
title: "Mount NTFS partition permanently"
date: 2008-06-05
forum: Hardware
---

### Post by DexterLB on 2008-06-05
In gutsy my NTFS partition mounted at startup. Now, when I upgraded to hardy It isn't mounted (I can mount it from nautilus or with the FS mounter applet), but I want it to be mounted permanently because my mother uses it and she always forgets to mount it and gets an error message. Is this possible? :confused:

---

### Post by BlueSkyNIS on 2008-06-05
Hi

You should try reading [*this thread*]("http://ubuntuforums.org/showthread.php?t=766688&highlight=automount+partitions").

---

### Post by mrMango on 2008-06-05
You should be able to simply add an entry to /etc/fstab

---

### Post by kpkeerthi on 2008-06-05
```
sudo apt-get install ntfs-config
```

Just launch ntfs-config from the menu (it should be under in Applications->System Tools) or via the terminal :

```
gksu ntfs-config
```

If your NTFS partitions are not yet configured, it will ask you to choose a name that will be use as mount point. Just put the name you want. Then just enable write support for internal and/or external device, and that is all.

---

### Post by BlueSkyNIS on 2008-06-05
> **kpkeerthi said:**
> ```
sudo apt-get install ntfs-config
```

Just launch ntfs-config from the menu (it should be under in Applications->System Tools) or via the terminal :

```
gksu ntfs-config
```

If your NTFS partitions are not yet configured, it will ask you to choose a name that will be use as mount point. Just put the name you want. Then just enable write support for internal and/or external device, and that is all.

But! You must unmount partitions first, or the ntfs-config will not show them.

---

### Post by DexterLB on 2008-06-06
> **kpkeerthi said:**
> ```
sudo apt-get install ntfs-config
```

Just launch ntfs-config from the menu (it should be under in Applications->System Tools) or via the terminal :

```
gksu ntfs-config
```

If your NTFS partitions are not yet configured, it will ask you to choose a name that will be use as mount point. Just put the name you want. Then just enable write support for internal and/or external device, and that is all.

It mounts the partition, when my a-mule download finishes I'll restart the PC and see if it's still mounted

---

### Post by DexterLB on 2008-06-06
It works!!! Thanks :popcorn:

---

### Post by jabalabar on 2008-12-11
It worked for me too, also this tweak repaired avi/video display problem with vlc (slow and crunching display) in fullscreen mode! 
Thnx a lot
:popcorn:

---

