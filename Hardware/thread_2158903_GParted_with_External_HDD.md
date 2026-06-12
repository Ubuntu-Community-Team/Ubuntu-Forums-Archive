---
title: "GParted with External HDD"
date: 2013-07-01
forum: Hardware
---

### Post by indianwala on 2013-07-01
Hi Friends,
I need ur help. I have 80 GB External HDD which was blocked after SCAN & FIX with Windows, after Google i found some tips so i tried with ubuntu. installed gparted and found my 80 GB HDD shows with two partitions as there is no Partitions in the 80 hdd refer the attachment . when i run the fdisk command only one partions show's. Please help how to correct the ntfs partion and get me data back safely.

---

### Post by carl4926 on 2013-07-01
It doesn't look like there is data in the ntfs partition, but that could be like that because it's corrupted.
There is a repair option in gparted but not sure if it works on ntfs?
Just be clear and tell us what windows does with this drive now?

The more you play with it the more difficult it will be to recover the data.
Tools for that are such as TestDisk

---

### Post by dandnsmith on 2013-07-01
This is the same topic as [this thread](http://ubuntuforums.org/showthread.php?t=2157760&page=2) which you already have answers in.

---

### Post by oldfred on 2013-07-01
Not sure if same issue, other thread is recovering data.

If you have an efi partition with boot flag that is usually for UEFI and then drive is gpt partitioned. Fdisk is only for MBR(msdos) drives. You can download gdisk which is for gpt drives.
sudo apt-get install gdisk

What does gparted say about partition, if you click (right click) on red icon? It probably will just say you need chkdsk from Windows. And you cannot run repairs from Linux, you need Windows to run chkdsk. Also chkdsk does not fix everything on one pass, so you have to run until there are no errors.

---

