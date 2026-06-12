---
title: "Devicekit is too inconvenient tool for me.."
date: 2009-11-01
forum: Hardware
---

### Post by koxel on 2009-11-01
Hello :)
I have replaced my debian desktop with 9.10 karmic..
It replaced HAL to Devicekit, but it's a too bad tool for me..

I usually used to mount ntfs partitions with gnome-mount at login time.
When mount partition, i checked remember mount status. So when the next login, gnome-mount automatically mount ntfs partitions..

But in karmic, gnome-mount doesn't mount partition automatically and i must mount partitions manually before i run applications using those partions..

Also devicekit is can't specify umask, permission of mounted partition, and charset and etc...
Only can change partitions label. It is too inconvenient..
nautilus-share require that  Shared folder has read permission by others. But ntfs partition mounted by gnome-mount with devicekit is only allow 700 permission. Even then root don't change permission..

I think Devicekit is incomplete tool and It is not yet usable.

Thanks for reader. And sorry to my poor english..

---

### Post by nikogawa on 2009-11-08
Has anyone found a way to change permissions on automatically mounted devices without changing /etc/fstab?

udev doesn't work, mount_options in gconf doesn't work either

---

### Post by maekloev on 2009-11-18
maybe [this]("http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic") will help you to auto-mount partitions at login-time. i was bothered by the same problem recently. that advice helped me fix it. :)

concerning permissions:
is it even possible to change permissions of files on an ntfs-drive? since permissions in windows aren't handled the same way as they are in linux, i don't think so. hence, this also makes it impossible to share files on an ntfs-partition.
but that is just my opinion. maybe there's a way i haven't figured out yet.

---

