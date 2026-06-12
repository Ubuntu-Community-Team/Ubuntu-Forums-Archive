---
title: "Mounting a vfat partition with FULL PERMISSIONS for ALL users..."
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by Hikaru79 on 2005-03-05
Hello... I have a vfat partition on my hard drive that is being used as a shared partition for Windows and Ubuntu. However, at the moment, I'm having to use 'sudo' every time I want to write to it, etc, which is really annoying. It mounts fine, I'm just wondering what I can do so that ALL users have FULL PERMISSIONS on this partition. Here is it's /etc/fstab entry:
```
/dev/hda6       /windows        vfat    defaults,users        0       0

```

Any ideas? Thanks in advance =)

---

### Post by GilGalad on 2005-03-05
That's my entry in /etc/fstab...

/dev/hda5       /mnt/windows    vfat    user,auto,exec,rw,umask=0000,gid=0 0 0

---

### Post by bored2k on 2005-03-05
[QUOTE=Hikaru79]Hello... I have a vfat partition on my hard drive that is being used as a shared partition for Windows and Ubuntu. However, at the moment, I'm having to use 'sudo' every time I want to write to it, etc, which is really annoying. It mounts fine, I'm just wondering what I can do so that ALL users have FULL PERMISSIONS on this partition. Here is it's /etc/fstab entry:
```
/dev/hda6       /windows        vfat    defaults,users        0       0

```

Any ideas? Thanks in advance =)[/QUOTE]
 for automount add this to ur fstab
 /dev/hda6       /media/windows    vfat    umask=000       0       0

---

### Post by Hikaru79 on 2005-03-05
[QUOTE=GilGalad]That's my entry in /etc/fstab...

/dev/hda5       /mnt/windows    vfat    user,auto,exec,rw,umask=0000,gid=0 0 0[/QUOTE]

Worked like a charm! Thanks, GilGalad.

---

