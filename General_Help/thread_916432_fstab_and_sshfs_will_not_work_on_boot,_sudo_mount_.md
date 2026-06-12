---
title: "fstab and sshfs will not work on boot, sudo mount -a works after boot"
date: 2008-09-10
forum: General Help
---

### Post by wilbbe01 on 2008-09-10
I am trying to get fuse/sshfs to mount a share on boot.  I have the entry added to fstab and it works fine when running sudo mount -a.  I don't see what should be any different between the two situations.  Does anyone have any idea?  Thanks.

In case that was not clear enough with the title.  On boot I have no luck with the mount, but after I log in I can run sudo mount -a fine with no errors, and a successful mount.  Thanks

---

### Post by rsambuca on 2008-09-10
You might have to add the command to the Sessions section of the gnome startup.

---

### Post by wilbbe01 on 2008-09-11
Thanks for the advice, it does work that way.  I wish I could get it to work when everything else in fstab is mounted, but I guess this will do until I look into things further.  I have a cifs share mounting a line before the sshfs share so it can't really be a lack of network at that point.  Oh well, for now I have modified fstab to allow my user to mount it, modified /etc/fstab.conf to allow an option on mount for non root users, and added it to services.

---

### Post by Vivaldi Gloria on 2008-09-11
See my posts here: [[COLOR="Sienna"]sshfs[/COLOR]]("http://ubuntuforums.org/showthread.php?t=896474")

---

### Post by wilbbe01 on 2008-09-22
Originally By Vivaldi Gloria
> See my posts here: sshfs


Originally By wilbbe01
> ...it works fine when running sudo mount -a
Thanks for your help, but as I stated in the beginning I already am sure the command works and is set up in fstab correctly (hence the functionality of the command mount -a).  Thanks for your suggestion though.

---

### Post by Vivaldi Gloria on 2008-09-22
If you use "noauto" in fstab it will not mount automatically. You need to use "auto" to mount it automatically. But this may not work with sshfs because it may try to mount it before a network connection is established. Better way is to mount it when a network connection is available. To do it that way see the post I mentioned above.

---

