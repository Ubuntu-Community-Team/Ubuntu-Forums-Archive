---
title: "A Couple HDD questions"
date: 2011-04-07
forum: Hardware
---

### Post by dniMretsaM on 2011-04-07
I have an external HDD that I converted from an internal hard drive from an old laptop and I have a couple questions.

1) It has 3 partitions (one is 38 GB FAT, one is 1.6 GB Free, and one is 1.6 GB Extended) that I assume are left over from when it was used as an internal because I never manually added them. I want to combine them but I can't figure out how. I've looked around some, but no luck.

2) How can I store files over 4 GB (minus 1 byte?)? I know I could before, but I can't now. I read somewhere that this could have to do with the type (FAT), so what should I format it to so that it will allow larger files? And if I need an extra tool, what is it/where can I get it?

---

### Post by An Sanct on 2011-04-07
> **dniMretsaM said:**
> I have an external HDD that I converted from an internal hard drive from an old laptop and I have a couple questions.

1) It has 3 partitions (one is 38 GB FAT, one is 1.6 GB Free, and one is 1.6 GB Extended) that I assume are left over from when it was used as an internal because I never manually added them. I want to combine them but I can't figure out how. I've looked around some, but no luck.

Use gparted
```
sudo gparted
```The tool has a great GUI, that will help you. Basically, just click the partition, you wan to operate with and select the operation.

> **dniMretsaM said:**
> 2) How can I store files over 4 GB (minus 1 byte?)? I know I could before, but I can't now. I read somewhere that this could have to do with the type (FAT), so what should I format it to so that it will allow larger files? And if I need an extra tool, what is it/where can I get it?
FAT has a limitation in file size, change the format to NTFS or EXT. NTFS is normally used if you want to use the disk with windows also.

So to join the answers: run gparted, delete the empty partition (make sure it is empty and you don't lose anything, select the 38Gb FAT partition, convert it to NTFS or EXT, select it again and "move/resize" it to occupy the whole space.

PS. Note that gparted is a powerful tool, double-check everything you do!

---

### Post by dniMretsaM on 2011-04-08
I installed GParted but when I tried to modify the FAT32 partition, it gave me an error saying that it needed dosfstools and mtools to work but when I tried to install them (sudo apt-get install dosfstools, sudo apt-get install mtools) it said they are both the latest version. Then I tried formatting it to ext2, but it said I needed e2fsprogs. When I attempted to install it, same thing. Already up to date. Same with ext4. It gave me a minimum version number, and I checked to see if maybe the "latest" version wasn't high enough, but it was. So I'm currently without ideas. Help would be greatly appreciated!

---

### Post by dniMretsaM on 2011-04-09
Bump + pictures. I took some screen shots to show in case I'm missing something. The first one is the File System Support screen in GParted which says it supports ext4 (which is what my HDD is). The second shows the info about my HDD and it says it needs e2fsprogs 1.41+ to be installed to work with ext4. The third is showing that it IS in fact installed.

EDIT: I decided to reinstall GParted and it appears to be working.

---

### Post by An Sanct on 2011-04-10
Okay, I have slightly lost track of this issue, so I'll try to help "on the fly".

Create a Live USB with the boot usb creator and make sure, the drive is not mounted, before making changes.

Sorry for the short reply/answer, I haven't got time right now.

PS. I never had problems with gparted yet ... those problems are realy strange... maybe it's a bug?

---

### Post by dniMretsaM on 2011-04-10
I guess you didn't read my edit. I fixed it by reinstalling GParted Some file must have been corrupted or something because now it works. Thanks for the help.

---

### Post by IcarusR on 2011-04-10
> I guess you didn't read my edit. I fixed it by reinstalling GParted Some file must have been corrupted or something because now it works. Thanks for the help. 

Would have helped if you marked the thread as Solved from the 'Thread Tools' menu.

Perfect example of why we should all do this !

---

### Post by dniMretsaM on 2011-04-10
I can't figure out how to edit the prefix. Sorry.

---

### Post by An Sanct on 2011-04-13
On top of the thread you have "thread tools", that is a drop down menu, that has a "mark as solved" entry.

---

