---
title: "Can't Mount FAT Partition"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by obvious_ron on 2005-07-24
[FONT=Georgia]I am trying to mount a FAT partition, but whenever I try to accesss it through Konquerer, I get this error:
> Could not mount device.
The reported error was:
mount: can't find /dev/hdb5 in /etc/fstab or /etc/mtab
Any ideas?[/FONT]

---

### Post by PeP on 2005-07-24
[QUOTE=obvious_ron][FONT=Georgia]I am trying to mount a FAT partition, but whenever I try to accesss it through Konquerer, I get this error:

Any ideas?[/FONT][/QUOTE]
did you add this line to your fstab (replace pep by your username)?

/dev/hdb5      /mnt/hdb5        vfat    defaults,user,uid=pep,gid=pep       0       0

---

### Post by obvious_ron on 2005-07-24
[QUOTE=PeP]did you add this line to your fstab (replace pep by your username)?

/dev/hdb5      /mnt/hdb5        vfat    defaults,user,uid=pep,gid=pep       0       0[/QUOTE]

Where do I find my fstab?

---

### Post by obvious_ron on 2005-07-24
Okay, I found fstab, but only root has permission to write.  I'm guessing I need to edit it via sudo.  How do I do this?

---

### Post by manicka on 2005-07-24
[QUOTE=obvious_ron]Okay, I found fstab, but only root has permission to write.  I'm guessing I need to edit it via sudo.  How do I do this?[/QUOTE]
 in a terminal 

```
sudo gedit /etc/fstab
```

---

### Post by varunus on 2005-07-24
Or, since you're using KDE, "sudo kwrite /etc/fstab" in a terminal.

---

