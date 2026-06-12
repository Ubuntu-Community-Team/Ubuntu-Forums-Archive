---
title: "PSP mounting Read only"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by liquid8d on 2006-06-17
Hello,

 I am having some issues with my psp mounting as read only. I have seen some threads on this before, but they seemed to be slightly different issues.

If I have my psp usb on when booting, it mounts fine, as read/write. However, if I turn it off, and it is remounted, it becomes read only.

Here is what mount looks like on boot:

```

/dev/sdb1 on /media/psp type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

Regardless of whether I eject or not, on remount it becomes readonly

After re-mount:
```

/dev/sdc1 on /media/psp type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

After manual re-mount:

```

/dev/sdc1 on /media/psp type vfat (rw)

```

If I try to take ownership or chmod once it has been re-mounted, it says it is a readonly filesystem:

```

sudo chown -R tim /media/psp
chown: changing ownership of `/media/psp/memstick.ind': Read-only file system
chown: changing ownership of `/media/psp/mstk_pro.ind': Read-only file system

sudo chmod 777 -r /media/psp
chmod: cannot access `777': No such file or directory
chmod: changing permissions of `/media/psp': Read-only file system

```

Sometimes, even after ejecting, it does not re-mount to the same device. Also, in nautilus after a remount, sometime it does, sometimes it doesn't show locked icons, but it will not let me create folders or files either way.

I have also tried modifying fstab to specify umask, but still it doesn't seem to take (not sure it is even using it with automount to be honest)

Any ideas?

---

### Post by bodyhead on 2006-06-17
I was having the same problem but I solved it by following the instructions in the following post

[http://ubuntuforums.org/showthread.php?t=58380]("http://ubuntuforums.org/showthread.php?t=58380")

---

### Post by liquid8d on 2006-06-18
sorry, tried the above with same issue... 

```

/dev/sdb1 on /media/psp type vfat (rw,noexec,nosuid,nodev,shortname=winnt,user=tim)

rm: cannot remove `Q2dm5.bsp': Read-only file system

```

I had since added root access, because of wanting to use swat for smb configuration, and I have noticed now that i can in fact write using root access. So it appears this is a user permissions problem.

I can probably temporarily have it mount as root, or give my login root access, Any ideas why this may occur? Why would a user not have access to write to a drive that is mounted as read/write? I have seen others that say they do not have this problem on dapper.

EDIT: stranger even still, I actually rebooted after attempting the above, and after unmounting/re-mounting, I was able to create a folder, but a few seconds later, when I tried to delete the folder, it changed to read only.

---

