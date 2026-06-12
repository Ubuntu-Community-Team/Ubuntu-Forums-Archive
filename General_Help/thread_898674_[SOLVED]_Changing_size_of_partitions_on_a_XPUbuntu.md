---
title: "[SOLVED] Changing size of partitions on a XP/Ubuntu dual boot"
date: 2008-08-23
forum: General Help
---

### Post by plesset on 2008-08-23
At work I have a dual boot with XP first (NTFS), then Ubuntu and a shared FAT32 partition, which is used to share my music between the two systems. Basically I followed [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) and it has work fine for me. But unfortunately I was a little bit cheap with the size of the NTFS partition and now I need to enlarge it. Is it save for me to use a systemrecuseCD with gparted to first shrink the ubuntu partition and then increase the NTFS to file the gap? Or is there any other more preferred way?

Thanks!
MP

---

### Post by qstraza on 2008-08-23
thats the best way.

---

### Post by Elfy on 2008-08-23
No that sounds like what I would do, if you used the guided option then it's likely that the buntu partition is in an extended - although I am not sure of the gparted version on systemrecue and actually use partedmagic.

IF it is an extended you need to resize the ubuntu partition, then resize the extended before the space will be available to add to the ntfs partition.

If you get a problem the next time you boot buntu it could be down to changing UUIDs - you can edit the fstab file at the root prompt if necessary.

---

### Post by plesset on 2008-08-23
Thanks all - I guess I know what I'll be doing first thing Monday morning.

---

### Post by Elfy on 2008-08-23
Thought I'd put this here - just in case you need it at work :D

If you do need to change the UUIDs you can do so from the root prompt in recovery mode. To get the UUID run
```
blkid
```
Make sure that the item you are trying to boot has the correct UUID and that fstab is correct.

You can see here in mine

blkid - ```
/dev/sda1: UUID="[COLOR="Red"]ccf8f1c4-97d0-4544-a0ee-04088d5d67a9[/COLOR]" 
```

menu list -  ```
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=[COLOR="#ff0000"]ccf8f1c4-97d0-4544-a0ee-04088d5d67a9[/COLOR] ro
```

fstab - ```
# /dev/sda1
UUID=[COLOR="Red"]ccf8f1c4-97d0-4544-a0ee-04088d5d67a9[/COLOR]
```

If you need to edit you will have to use nano, to save - Ctrl+O, enter , to exit Ctrl+X

You won't need sudo in recovery mode

```
nano /boot/grub/menu.lst
nano /etc/fstab
```

Also check your swap partition in blkid and fstab.

---

