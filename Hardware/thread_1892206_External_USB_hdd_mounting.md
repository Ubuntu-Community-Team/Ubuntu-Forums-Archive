---
title: "External USB hdd mounting"
date: 2011-12-07
forum: Hardware
---

### Post by yoramdavid on 2011-12-07
Hello all,

I am using Ubuntu 11.10 gnome-classic. Dolphin file manager.
I have an external hardrive (USB).
I do not want to mount the hdd automatically as it is not always plugged in.
But when mounting it, I do not want the windows hidden and system files to appear.
For that effect, I have an entry that looks like this:
```
#Entry for /dev/sdb1 :
UUID=3C607E73607E342C	/media/Yoram-A-Data	ntfs-3g	users,user,nosuid,nodev,locale=pt_PT.UTF-8,windows_names,hide_hid_files,noauto	0	0
```

But when I want to mount the hdd, I get the following error:
```
Ocorreu um erro ao aceder ao 'Yoram A-Data'; o sistema devolveu: A operação pedida foi mal-sucedida.: Error mounting: mount exited with exit code 1: helper failed with:
Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged
```

How do I remove the setuid/setgid bit from the binary?
I have tried to rebuild NTFS-3G with integrated FUSE support and make it setuid root, but that did not seem to have succeeded.

There is a space in the hhd name, is that a problem? I have no space in the mount directory.
I have renamed the hdd, so it has no space in the name, still the problem persists.

If I open Dolphin as root, I can then mount it no problems

Regards.

Yoram

---

