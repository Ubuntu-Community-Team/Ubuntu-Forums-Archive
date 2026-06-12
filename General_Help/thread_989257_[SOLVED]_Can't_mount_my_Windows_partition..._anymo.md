---
title: "[SOLVED] Can't mount my Windows partition... anymore!"
date: 2008-11-21
forum: General Help
---

### Post by GlenboLake on 2008-11-21
I used to mount my Windows drive automatically when Ubuntu started up.  The relevant chunk of fstab is

```

# /dev/sda1
/dev/sda1	/media/windows	ntfs	nls=utf8,user,umask=000,rw 0	0
# UUID=0010B08410B081E8	/media/windows	ntfs	uid=user
```

Starting yesterday, though, I can't mount it at all.  When I try to, I get a popup error:
[IMG]http://i7.photobucket.com/albums/y299/GlenboLake/Uncategorizable/Screenshot-gnome-mount.png[/IMG]

So I followed the (short) instructions at the link, which pretty much only said to put ```
  chown root $(which ntfs-3g)
  chmod 4755 $(which ntfs-3g)
``` in a terminal.  I still get that exact error though.

I'm pretty sure the only thing I've done that would have any effect on this is run the Update Manager, and the last update I did was just hplip and related packages.

Thanks in advance.

---

### Post by Bucky Ball on 2008-11-21
Reboot into Windoze and do a clean *shutdown* (not restart). Then give it a try.

---

### Post by taurus on 2008-11-21
What if you try to mount it from a terminal with

```
sudo mount -t ntfs-3g /dev/sda1 /media/windows
df -h
```

---

### Post by GlenboLake on 2008-11-21
The clean shutdown worked! Thanks :)

---

### Post by Bucky Ball on 2008-11-22
> **GlenboLake said:**
> The clean shutdown worked! Thanks :)

Great news! Let's hope that does the job permanently. Could you mark this thread as 'Solved' from 'Thread Tools' at the top right, please. Others might then find a fix here. :)

---

