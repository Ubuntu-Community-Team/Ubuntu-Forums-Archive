---
title: "Mounting smbfs throught nautilus?"
date: 2008-08-11
forum: General Help
---

### Post by Fixman on 2008-08-11
I have a Windows machine connected by LAN to my Ubuntu Comp, and to access it I use Samba. I recently installed Smbfs (makes you able to mount a Windows share as it was a partition) and it works perfectly. I set it to "auto" on my fstab so when I turn on my PC it automatically mounts. However, if the other computer (with windows) is turned off, the "partition" doesn't mount (this is logical, and the expected solution). So, to access the partition on my other computer, I must turn it on, and re-mount it using the terminal. However, is there a way to nautilus treat the unmounted "partition" as it treats internal HDs, by putting an icon when its unmounted? (or something that *may* look like that)?

---

### Post by cariboo on 2008-08-11
you can try in the Nautilus Address bar:

```
smb://<windowscomputer>/<shareddirectory>
```

If you don't see the address bar in Nautilus click the toggle button on the left side. This will not mount it to your usual mount point, but it is accessable.

Jim

---

### Post by Fixman on 2008-08-11
> **cariboo907 said:**
> you can try in the Nautilus Address bar:

```
smb://<windowscomputer>/<shareddirectory>
```

If you don't see the address bar in Nautilus click the toggle button on the left side. This will not mount it to your usual mount point, but it is accessable.

Jim

PLEASE read my post. I would make a bookmark if I would want to do what you are saying. I mean mounting a share (that is on fstab) by smbfs using a button.

---

### Post by loboc on 2008-08-11
check this post to create a shortcut to it in the  Places that mounts it if its not mounted. 
The icon wont go away if the PC isnt on because it doesnt poll it until to you click on it to open it

you can use this in lieu of the fstab entry

[http://ubuntuforums.org/showpost.php?p=5537005&postcount=5](http://ubuntuforums.org/showpost.php?p=5537005&postcount=5)

---

### Post by Fixman on 2008-08-11
> **loboc said:**
> check this post to create a shortcut to it in places that mounts it if its not mounted

you can use this in lieu of the fstab entry

[http://ubuntuforums.org/showpost.php?p=5537005&postcount=5](http://ubuntuforums.org/showpost.php?p=5537005&postcount=5)

I use smbfs because I want to be able to access the shares by the terminal, so this won't work.

---

### Post by loboc on 2008-08-11
you can still leave the mounts in fstab with no auto and mount them their manually too kinda defeats the point, you want a conditional icon,

if you can keep the mounted drive from displaying on the desktop in the nautilus preference or something
then you can make a symlink to /media/mountpoint on the desktop you can change the icon to a hd image it would be there all the time

maybe playing with emblems would give you the conditonal aspect conditonal

---

### Post by Fixman on 2008-08-11
> **loboc said:**
> you can still leave the mounts in fstab with no auto and mount them their manually too kinda defeats the point, you want a conditional icon,

if you can keep the mounted drive from displaying on the desktop in the nautilus preference or something
then you can make a symlink to /media/mountpoint on the desktop you can change the icon to a hd image it would be there all the time

maybe playing with emblems would give you the conditonal aspect conditonal

Oh man, I feel ununderstanded.
I want an icon on the main nautilus window (NOT THE DESKTOP) so I don't have to type on alt+f2 or the terminal mount -a each time I want to mount it. I don't really have a problem with it, I just want it to feel like a regular HD.

---

### Post by doas777 on 2008-08-11
check out [this thread]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") on mounting SMB\CIFS shares in ubuntu. I think that is what you are looking for.

good luck
franklin

---

