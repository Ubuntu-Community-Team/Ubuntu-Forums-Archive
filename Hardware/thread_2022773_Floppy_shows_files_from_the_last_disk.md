---
title: "Floppy shows files from the last disk"
date: 2012-07-11
forum: Hardware
---

### Post by pjungwirth on 2012-07-11
I'm trying to go through some old files on 3.5" floppies, using Xubuntu 12.04. The floppy drive works, and I can read the disks on Windows. I can also read the first 2-3 on Xubuntu, like this:

```
    udisks --mount /dev/fd0
    ls /media/floppy0
    udisks --unmount /dev/fd0
```But after looking at 2-3 floppies, the system seems to get stuck on the last-viewed floppy. After that, mounting & unmounting appear to work, but `ls` keeps showing the contents of one of the previous disks. Once that happens, I have to reboot the machine to start reading floppies again. It's as if the floppy contents are cached somewhere and that isn't getting cleared. Is there a way to tell the system that it needs to re-read the data from the disk?

---

### Post by sudodus on 2012-07-11
Have you tried the basic mount and umount commands? See this link.
[[COLOR="Red"]_http://linux.about.com/od/linux101/l/blnewbie4_2_3.htm_[/COLOR]]("http://linux.about.com/od/linux101/l/blnewbie4_2_3.htm")

Maybe it is important to let the system synchronize before unmounting.
```
mount -t auto /dev/fd0 /mnt/floppy
```
Do what you want and after that
```
umount /mnt/floppy
```
and maybe [FONT="Courier New"][SIZE="3"]cd[/SIZE][/FONT] and maybe [FONT="Courier New"][SIZE="3"]sync[/SIZE][/FONT]
and the eject the floppy.

---

### Post by pjungwirth on 2012-07-11
Thank you for your reply. Alas, `mount` doesn't work at all; you have to use `udisks --mount`. I don't understand why, but there are at least a dozen threads here recommending udisks as the solution. Here is one:

[URL="http://ubuntuforums.org/showthread.php?t=1693556"]http://ubuntuforums.org/showthread.php?t=1693556
[/URL] 
On the other hand, both `udisks --unmount` and `umount` successfully unmount the drive.

I tried using `sync`, but that had no effect. Neither did `cd /media/floppy0 && ls`.

---

### Post by sudodus on 2012-07-12
I see now that you are new at the Ubuntu Forums. Welcome :-)

I understand that you have already browsed the internet and tried a few commands. It was so long ago that I used floppies, so I can't come up with some better detailed solution. Probably floppy reading has low priority during development of new versions of linux.

One obvious solution is to ***use what works***:

1. You wrote that Windows works.

2. But if you really want to use linux, I suggest that you try either some old version of Ubuntu or some other linux distro, for example Knoppix, that is known for good hardware detection. Or the micro distro DSL. You can (and should) run them live, booted from CD or USB, while you are testing.

[[COLOR="Red"]_http://old-releases.ubuntu.com/releases/_[/COLOR]]("http://old-releases.ubuntu.com/releases/")

[[COLOR="red"]_http://knopper.net/knoppix-mirrors/index-en.html_[/COLOR]]("http://knopper.net/knoppix-mirrors/index-en.html")

[[COLOR="Red"]*http://www.damnsmalllinux.org/download.html*[/COLOR]]("http://www.damnsmalllinux.org/download.html")

---

