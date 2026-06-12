---
title: "[SOLVED] Recover Deleted files on NTFS partition with Live CD"
date: 2008-09-16
forum: General Help
---

### Post by juanoleso on 2008-09-16
The title says it all.  Is there a program that I can use to possibly recover deleted files on an NTFS partition?  I'd like to run it from a Live CD.

---

### Post by unutbu on 2008-09-16
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Look for the Ntfsundelete program which is part of ntfsprogs package.

To run it from a LiveCD, you might need an internet connection, or a USB Flash drive to install the ntfsprogs package first.

---

### Post by lswest on 2008-09-16
Also, check this out: [http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/) it's a very nice how-to (thanks to aysiu)

---

### Post by az on 2008-09-16
You can use Ubuntu-rescue-remix if you need a lean live cd (or live USB) system.

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

It's command-line only and requires very limited resources, so you can run it on older computers.

---

### Post by juanoleso on 2008-09-24
Just an Update:

I used the Ubuntu Remix CD to boot live.  I then installed smbclient and smbfs and mounted a remote share on a windows computer (only have M$ at work).  I ran photorec on the partition under scrutiny and selected to scan the whole drive (scanning just free space immediately came back with a segmentation fault).  I sent the data to the remote computer.  I was able to recover A LOT of data.  I had to pause photorec multiple time so that I could delete garbage files that it found so I wouldn't run out of space on the remote computer.

Thanks everybody

---

