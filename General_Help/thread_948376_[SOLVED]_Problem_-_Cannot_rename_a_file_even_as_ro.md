---
title: "[SOLVED] Problem - Cannot rename a file even as root"
date: 2008-10-15
forum: General Help
---

### Post by tomasGM on 2008-10-15
Hi all.  I have a big problem.  After having a crash last night of KTorrent I find that I cannot rename, cut, delete any file anywhere on my system even when logged in as root.

I have used Nautilus as root using sudo and gksudo and no joy.

Logging into KDE 3.5 allows the right-click option to rename but the rename fails again even using the "Open as Root" option in the Dolphin.

HELP.

---

### Post by Sycron on 2008-10-15
What file do you rename ? If it's not a vital system file you can become again the owner of that file with ```
sudo chmod 777 name-of-the-file.extension
```.

You won't need then to edit it with a super user permission.

---

### Post by tomasGM on 2008-10-15
After several reboots I now seem to be able to work in the Linux partition (before no) and am now having problems only in the Windows partition.

Actually I was trying to rename a folder in the Windows partition and could not was how I discovered the problem initially.

Now am looking to see if I can fix the Windows problem.

---

### Post by Sycron on 2008-10-15
A Windows partition is not able to retain access rights of a file.

---

### Post by tomasGM on 2008-10-15
Apparently something go messed up as a result of the crash and it looks like I have fixed things using Storage Device Manager.

Thanks a lot.

---

### Post by geirha on 2008-10-15
Did the new name you tried to put on the folder have any special characters in them? Windows disallows certain characters that have special meaning in filenames, for example the question mark (?) which is used in patterns. Linux in turn will by default also disallow these characters on NTFS and FAT filesystems.

---

