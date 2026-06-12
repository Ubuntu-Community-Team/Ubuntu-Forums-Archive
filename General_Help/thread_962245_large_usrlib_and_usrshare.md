---
title: "large /usr/lib and /usr/share"
date: 2008-10-29
forum: General Help
---

### Post by Mattz0r on 2008-10-29
Hi, i'm trying to slim down my filesystem because I don't have alot of room on this old computer i'm using it on. It seems /usr/lib and /usr/share are both in the 650-700MB range, so they are the largest dirs. How can I make them smaller? i don't understand the stuff that is in them.. and is there anything else i can cut back on?
5.2M    bin
36M     boot
0       cdrom
116K    dev
11M     etc
2.6G    home
0       initrd
0       initrd.img
0       initrd.img.old
242M    lib
0       lost+found
0       media
0       mnt
0       opt
0       proc
46M     root
6.7M    sbin
0       srv
0       sys
33K     tmp
1.5G    usr
231M    var
0       vmlinuz
0       vmlinuz.old
4.6G    total

---

### Post by scragar on 2008-10-29
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

I wouldn't recomend deleting anything you are unsure about. /var can normaly be cleaned out a little(any .gz file is an old version you won't need: ```
sudo rm /var/log/*.gz
```), but that's about it other than uninstallign things you don't need.

---

