---
title: "Need more space"
date: 2008-08-21
forum: General Help
---

### Post by farmdve on 2008-08-21
I have Windows and Ubuntu
Before installing ubuntu i thought 4,300 GB would be sufficient however due to updates and soft i've got only 980MB free maybe less
If i use partition magic in windows to resize my D: partition how do i add the space to ubuntu?
Or is it possible?

---

### Post by becatlibra on 2008-08-21
You are going to be better off getting an ISO of Gparted Live (or another Live CD with GParted included).

The GParted disc will boot right into the interface for resizing

I do not believe Partition Magic supports the ext3 file system.

---

### Post by linux_tech on 2008-08-21
Partition Magic 8 will recognize ext3 linux partition and resize it. It worked ok for me.  But I would recommend using Gparted instead on linux ext partitions. I have heard of possible boot issues after using partition magic on ext3 linux partitions.

---

### Post by farmdve on 2008-08-21
To use GParted i have to burn another CD?

---

### Post by fparedesg on 2008-08-21
You need to insert the Ubuntu Live CD you used to install Ubuntu. Boot from the CD. Once the desktop is loaded, just go over to the Terminal and type ```
sudo gparted
``` , and gparted will launch, which will allow you to resize the partition size. Once You're done, exit out of gparted and shut down. Eject the CD when it tells you to, and you're done.

[EDIT] Another thing you can do is to just install it into Ubuntu. Open terminal and type in ```
sudo apt-get install gparted
```once it finishes installing, you can run it with ```
sudo gparted
```

---

