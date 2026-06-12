---
title: "Problem with filenames with non-english characters in NTFS USB drive"
date: 2008-09-03
forum: General Help
---

### Post by gurlinux on 2008-09-03
Hi, I am quite a newbie, but I'm working on it :) 
I just installed Kubuntu 8.04 (64bit) and found that it detects, automounts and can access a NTFS USB external hard drive, even write to it with no need to modify anything.

Unfortunately, I need this external drive to continue being NTFS, as it is shared with Windows machines for various storing purposes (namely backups).

However, when copying to it folders or files with international characters (Spanish accented letters) I get an error and the operation aborts. 

I did my homework, searched all over the place, and found that KDE has an issue with international characters: [http://wiki.archlinux.org/index.php/HAL#Locale_issues](http://wiki.archlinux.org/index.php/HAL#Locale_issues)
I also found a solution for fixed drives: [http://ubuntuforums.org/showpost.php?p=41878&postcount=7](http://ubuntuforums.org/showpost.php?p=41878&postcount=7)
And supposedly found a solution for my scenario (USB external drives): [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4759465](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4759465)

Long story short, I tried this last link but either I did something wrong, or the HOWTO is wrong, as it made me destroy my /sbin/mount.ntfs and /sbin/mount.ntfs-3g files with symlinks that apparently pointed to nowhere. 
I managed to recover from that mess with the live CD (so I'm back where I started), but I need advice to understand if the HOWTO is wrong, or if there is another guide out there for this scenario... and specially written for newbies.

Thanks in advance!

---

### Post by gurlinux on 2008-09-08
Anyone? :confused:

---

### Post by rubioxtu on 2008-12-06
[http://ubuntuforums.org/showthread.php?p=4759465](http://ubuntuforums.org/showthread.php?p=4759465)

---

