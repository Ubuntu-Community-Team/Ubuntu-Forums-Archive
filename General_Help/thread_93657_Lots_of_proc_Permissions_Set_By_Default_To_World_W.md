---
title: "Lots of /proc/* Permissions Set By Default To World Writable?"
date: 2005-11-22
forum: General Help
---

### Post by SuSUntu on 2005-11-22
I recently installed Ubuntu to try it out and was running some security checks (and just poking around in general).

I noticed that when running this command:

```
sudo find / -perm -002 \( -type f -o -type d \) -ls > WorldWriteable.txt
```

that lots of directories and files in /proc were listed as world writable.

Scanning the output file, most of the files are in the /proc/*/attr directories (if not all); filenames in /proc/* are mostly (if not all of them) .../current, .../exec, and .../fscreate. The owners vary from root, to current user, to hal, etc. (see Examples section below)

I checked my Centos 4.x installation using the same test, and while the Ubuntu test resulted in hundreds of world writable files in /proc, the Centos test came back with a total of only 12 files (none in /poc). The only commonality between the two installations were these world writables (note the "rwt" which indicates read, write and store in swap space):

rwx-rwx-rwt /dev/shm
rwx-rwx-rwt /tmp/.X11-unix
rwx-rwx-rwt /tmp/.ICE-unix

Questions:

1. Can one presume that the world writables common to both Centos and Ubuntu are "normal" and should be left like this?

2. Conversely, should one presume that the Ubuntu permissions for the /proc files are too loose, and therefore they should be "chmod'd" to remove the write bit for "others"?

Thanks.
__________________

Examples from the Ubuntu permissions check:

-rw-rw-rw-   1 root     root            0 Nov 22 11:11 /proc/9464/attr/current
-rw-rw-rw-   1 root     root            0 Nov 22 11:11 /proc/9464/attr/exec
-rw-rw-rw-   1 root     root            0 Nov 22 11:11 /proc/9464/attr/fscreate
-----------
-rw-rw-rw-   1 [USER] [USER]        0 Nov 22 11:11 /proc/9106/task/9106/attr/current
-rw-rw-rw-   1 [USER] [USER]        0 Nov 22 11:11 /proc/9106/task/9106/attr/exec
-rw-rw-rw-   1 [USER] [USER]        0 Nov 22 11:11 /proc/9106/task/9106/attr/fscreate

While I'm at it, a few other questionable permissions:

----------
-rw-rw-rw-   1 root     root            0 Nov 22 11:11 /proc/acpi/hotkey/info
-rw-rw-rw-   1 root     root            0 Nov 22 11:11 /proc/acpi/hotkey/action
-rw-rw-rw-   1 root     root            0 Nov 22 11:11 /proc/acpi/hotkey/poll_config
-rw-rw-rw-   1 root     root            0 Nov 22 11:11 /proc/acpi/hotkey/event_config

----------

drwxrwxrwt   3 [USER] [USER]       72 Nov 18 16:02 /var/cache/fonts/pk/ljfour
drwxrwxrwt   4 [USER] [USER]       96 Nov 18 16:02 /var/cache/fonts/pk/ljfour/jknappen
drwxrwxrwt   2 [USER] [USER]      560 Nov 18 16:02 /var/cache/fonts/pk/ljfour/jknappen/ec
drwxrwxrwt   2 [USER] [USER]       80 Nov 18 16:02 /var/cache/fonts/pk/ljfour/jknappen/tc

---

### Post by LordHunter317 on 2005-11-25
Everything in /proc is virtual and exported by the kernel.  CentOS doesn't have such things because the RH kernels are patched to remove them.  I don't know if the wide permissions are actually a security issue or not, as many of those files are probably really read-only even if they have a write permission.

The /var/cache/fonts fiels I'm not sure about.

---

### Post by SuSUntu on 2005-11-25
Thank you for the input.

---

