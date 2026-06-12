---
title: "Wierd HardDrive Issues"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by Shakey_Jake33 on 2008-01-10
I've got 2 problems right now, neither particularly major, but still very annoying.

1) I have mutiple Hard Drives, and while some of my drives automatically mount on boot up, others do not.  The ones that do not automatically mount can be manually mounted, but require me to enter my password - which is probably why they will not automatically mount.
I've no idea what's different about these drives, they were formatted and created in Windows, but so were the drives which automatically mount fine.  All drives are NTFS.

2) When I delete files on these hard drives, they do not go in my Recycle Bin.  Instead, these files go into a hidden directory called something like '~trash.username'.  Why are they going there instead of the Recycle Bin?

3) Not strictly a HDD question, but sometimes files with Japanese file names do not show, and I have to go and rename them in Windows.  I have installed Japanese language support.
I also commonly find directories that finish with a '~' (note it's a wobbly hyphen) don't show unless I rename them in Windows.

I keep finding myself logging back into Windows to fix problems, and I'd like to one day remove Windows altogether.

Thanks

---

### Post by LaRoza on 2008-01-10
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

The Recycle Bin is a Windows directory for "deleted" files, .trash is the Linux area. It has nothing to do with the file systems, just the OS's.

~ is a special character in Linux, it means your home directory. It can't be used in file names just like slashes can't in Linux or Windows.

---

### Post by Shakey_Jake33 on 2008-01-10
I meant the linux 'Deleted Items' folder (just used to calling it Recycle Bin).  When I delete a file on the above mentioned drive, it does not appear in the Deleted Items on the desktop, but is in the hidden 'trash' folder.

Interesting to know about the ~ thing though, no biggie, just had to rename a few directories.  It appears *files* can include ~ though.

---

