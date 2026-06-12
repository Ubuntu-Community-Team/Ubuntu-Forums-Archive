---
title: "Mount without icon"
date: 2008-09-19
forum: General Help
---

### Post by ocascante on 2008-09-19
Hi,

I need to mount a shared folder in a user computer. 
For the best security, i need to have no folder icon and no folder name in the desktop computer of that user. 
Somebody knows how to mount a shared folder using fstab, but without creating a desktop icon and a folder name?

This is my actual fstab line:

//111.111.111.111/shared_folder /home/user/folder username=user,password=pas,workgroup=group,codepage=???,iocharset=??? 0 0

this instruction create a icon folder and name in the desktop computer.

Thanks

---

### Post by northern lights on 2008-09-19
The mounted volumes not showing on the desktop is not really related to either the fstab file or the mounting process itself. Rather you should be able to configure the specific user's desktop such that volumes are not drawn.

Run```
gconf-editor
```and uncheck "volumes_visible" under "/apps/nautilus/desktop/"

---

### Post by ocascante on 2008-09-19
Thanks for your help!!!

---

### Post by Vivaldi Gloria on 2008-09-19
> **northern lights said:**
> and uncheck "volumes_visible" under "/apps/nautilus/desktop/"

Note that that will also prevent usb disks and cds to appear on the desktop. The better way of mounting a filesystem without getting a desktop icon is to mount it to /mnt/mountpoint rather than /media/mountpoint.

---

### Post by stickmangumby on 2008-09-19
Welcome to the forums ocascante.

Please mark threads as solved if your problem is fixed.

Cheers,
stickmangumby

---

### Post by Meetloaf13 on 2008-11-11
Not sure if this thread is too old to revive, but I'm having the same exact problem.

I have that box deselected, and the icons still show on my desktop?

How do I go about changing the mount-point?

---

