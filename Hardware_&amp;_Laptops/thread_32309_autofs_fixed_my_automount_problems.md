---
title: "autofs fixed my automount problems"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by whistl on 2005-05-07
My ubuntu laptop runs primarily with only a wifi network connection.  But I use NFS to access my fileserver, and if I put the NFS filesystem in /etc/fstab, the mount fails at boot, because it's attempted before the pccard and wifi are brought up.

Also, I have a digital camera with Compact Flash card, and pc-card adapter.  When I insert the Compact Flash adapter, and have the appropriate entry in /etc/fstab, the filesystem mounts just fine, but I cannot umount it.  It's always busy (process "gam_server" which I guess is something to do with Gnome, but I'm not sure what - no manpage).

In addition, I tried adding two entries in /etc/fstab for my C: and D: windows xp partitions on the local drive, but for some inexplicable reason, with those entries in there, when I first login, gnome takes forever to initialize, and always pops up an error message saying "HAL failed to initialize".  Even though they had "noauto", they would always get mounted at boot time.

I got tired of always opening a root terminal, mounting editing /etc/fstab when I wanted

I installed the "autofs" package, and configured the /etc/auto.master file to point to two new map files, auto.dos and auto.fs.  Now, as my normal user, I just "cd /dos/c" or "cd /dos/d" or "cd /dos/e" (for the compact flash drive), and I can access those filesystems with no errors or login delays.  and "cd /fs/music" to access the /music partition on my fileserver.

Works great!

---

### Post by fopetesl on 2006-07-10
So far it hasn't worked for me. I have tried several ways to get a floppy mounted without any disk present in the drive, a la Mandrake, i.e. it's ALWAYS shown as mounted (albeit with supermount) regardless of a (new)disk being inserted or not.

autofs _may_ be a way around this but I haven't found any decent doc to tell me how to (a) attach it to the kernel or (b) control what and how it responds to its /etc/auto.master file.

I have several kernel files on my system:
(1) [COLOR="DarkGreen"]/lib/modules/uname -r/kernel/fs/autofs/autofs.ko[/COLOR]
(2) [COLOR="DarkGreen"]/lib/modules/uname -r/kernel/fs/autofs4/autofs4.ko[/COLOR]
but none are shown as running with```
ps -A | grep autofs
```and neither autofs or autofs4 are listed in any of the rc?.d or init.d directories.

(What's the difference between autofs.ko and autofs4.ko?)

---

