---
title: "gksudo nautilus - Permissions to hard drive"
date: 2009-06-18
forum: Hardware
---

### Post by dimis80 on 2009-06-18
I need to ask for your help regarding the permissions that i can give to my hard drive through nautilus...

The story goes like this:

I build a new server to my company (DELL poweredge T300) and i have the following disks:

1x DELL 250GB (for the OS) | /dev/sda
2x DELL 250GB - Hardware RAID1 (for my company files, documents etc) | /dev/sdc
1x DELL 500GB (for my backup) | /dev/sdb

The server will be a file server...

Anyway, I need to change my permissions to sdc because it gives me only root permissions and I cant make specific access folders for my user (ex. I need to create a folder name "Documents" and allow 2 or 3 people to read/ write.

When I use gksudo nautilus and i browse to my mount folder of sdc (/media/disk) I can see that the permissions can be of change but when I make the change it gives me back the root!!!

I need your help on this cause it's my final step for the server to be ready...

I made sdc with NTFS filesystem, ext3 but they still give me root permissions...

---

### Post by dimis80 on 2009-06-19
Any help????

---

