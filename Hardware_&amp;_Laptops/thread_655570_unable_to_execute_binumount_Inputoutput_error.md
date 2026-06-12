---
title: "unable to execute /bin/umount: Input/output error"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by huck416 on 2008-01-01
This is interesting. I have an external 40gb hd connecting via usb. Mounts normal via ```
sudo ntfs-3g /dev/sdb1 /media/hotdrive
``` and up to today would unmount via ```
sudo umount /media/hotdrive
``` However, now I get the following error message when I try to unmount the drive. ```
sudo: unable to execute /bin/umount: Input/output error

``` This is the same for a FAT32 usb thumb drive. When I put the drives in a different machine running the same Kubuntu 7.10, they mount and unmount fine so I'm thinking something's gotten messed up with my mount command.

I tried to copy the mount file from the good machine to my laptop but of course the /bin directory is a read only file system and as I still consider myself a newbie with linux, I'm hesitant to change the properties; I may really break something.

Anybody have any ideas on what else might be causing the umount errors? Thanks.

---

### Post by taurus on 2008-01-01
Are you sure that is how you mount an ntfs partition?  That doesn't even look right.

> sudo ntfs-3g /dev/sdb1 /media/hotdrive

```
sudo mount -t ntfs-3g /dev/sdb1 /media/hotdrive
```

---

### Post by huck416 on 2008-01-01
That's the way I've been doing it and it's worked fine for the last several months. As a follow up to my first post, I rebooted and on startup it failed the fsck and directed to run a manual fsck which I did. It found several errors in blocks, sizes, etc which I fixed all then restarted the system. Same problem only now the error when I try to unmount is ```
$ sudo umount /media/hotdrive/
/bin/umount: 1: $&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;U&#265;T$&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;&#65533;&#459;&#65533;&#65533;&#65533;E&#65533;tP&#65533;U&#265;$&#65533;T$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;E&#265;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;E&#65533;&#65533;&#65533;!&#1027;&#65533;&#65533;E&#65533;&#65533;&#65533;&#65533;u&#1029;&#65533;&#65533;v&#65533;&#65533;&#65533;&#65533;: not found
/bin/umount: 3: Syntax error: ")" unexpected
```I tried mounting with your syntax; the drive mounts fine but the same error appears when I try to unmount. The only thing I've tried to install recently was kdetoys which failed. Don't know why but it didn't install so I gave up on it. BTW, thanks for the quick response.

---

