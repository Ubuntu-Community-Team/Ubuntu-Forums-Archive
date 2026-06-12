---
title: "Removing corrupted directories and/or fixing affected external disk"
date: 2012-03-20
forum: Hardware
---

### Post by randal on 2012-03-20
Hey everyone.

I was trying to backup my files using an external NTFS drive when I accidentally unplugged the connection. Now, I have a directory in the external drive I can't remove. It says there's Input/output error when I try to do a rm.

I don't know to what extent this has affected the external drive but I'm guessing not so much since I can pretty much do things in it other than removing the affected directory.

I'm not sure how to approach this problem. Should I also run some checks to the disk? If ever how to I go about it? I tried fsck but it says there's no fsck.ntfs. Then ntfsfix but it says the volume is corrupted.

Thanks.

---

### Post by aps2012 on 2012-03-20
Hi,

It's not much of a suggestion, but I recommend finding any genuine Windows machine that has NT 5.0 or above (i.e. Windows 2000, XP, Vista, 7) and running [FONT=Courier New]chkdisk.exe[/FONT] or [FONT=Courier New]scandisk.exe[/FONT] at a command prompt. After NT has patched up any problems with the filesystem, you should be able to remove the directory from NT using the [FONT=Courier New]del[/FONT] command at the shell (or by using the UI).

On Linux, unmount and remount the drive in to make sure the cached i-node tables for file-system are cleared. It should remount at this point. If it does, backup anything you need on Linux.

If it doesn't remount, put it back into the Windows machine and perform the backup there to another NTFS USB drive, then just reformat the drive from NT. You can then return to Linux, partially restore your data from the backup you took and then continue from where your original backup failed.

Hope this helps.

Cheers.

---

### Post by randal on 2012-03-21
Thanks for the suggestion. The problem is, the only other system I have runs Mac OS. I'll probably just ask some of the people I know if I can borrow their Windows machine.

Anyway, if there are other suggestions, I'm open for them.

---

### Post by randal on 2012-03-23
Just an update. I found a Windows machine and ran [FONT="Courier New"]chkdsk[/FONT] to fix the problem on my external drive. Everything's fixed (it seems). Now, I think after backing up the contents, I'll just reformat it to HFS+.

Thanks.

---

