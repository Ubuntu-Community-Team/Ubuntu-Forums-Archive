---
title: "Cannot mount volume"
date: 2008-08-27
forum: Hardware
---

### Post by Colo2 on 2008-08-27
cannot mount volume
unable to mount new volume

When I plug my external hard drive in :(

How can I fix this?

---

### Post by Colo2 on 2008-08-27
PLEASE :(
Somone must have come up with this before!!!

---

### Post by Beth1957 on 2008-08-27
> **Colo2 said:**
> cannot mount volume
unable to mount new volume

When I plug my external hard drive in :(

How can I fix this?

Try opening a terminal window and typing (or copy/paste)
```
sudo modprobe -r ehci_hcd
```

Works for me, so good luck! You might have to do this every time you want to mount the hard drive, or you might not... Sometimes my hard drive etc mount automatically, sometimes they don't :rolleyes:

---

### Post by Whisper45 on 2008-08-27
Hey, i'm colos brother, my computer is the one that is having this problem

And thanks for the tip, but no such luck.

---

### Post by Whisper45 on 2008-08-30
no one has had this problem before? D:

---

### Post by WRDN on 2008-08-30
Open the Terminal, and type:

```
sudo fdisk -l
```

The disks and partitions will be listed. Find the device code for the external HDD (it will be /dev/sdaN or /dev/hdaN, where N represents a number).

Now, type:

```
sudo mkdir /media/files
```

If you wish, you can replace "files" with something else.

Now, type:

```
sudo mount /dev/[device] /media/files
```

This will mount the drive.

If it does not work, you could try force- mounting the drive.

```
sudo mount /dev/[device] /media/files -o force
```

---

### Post by Bliepo32 on 2008-08-30
Maybe you could post your fstab and mtab, That might be the problem. Also, we need more information to help you. Pelease answer these questions

[LIST=1]
[*]What is the brand and type of the external harddisk?
[*]Have you checked wether it works on other computers?
[*]How is the hd connected. By USB or firewire?
[*]What computer are you using?
[*]Which version of Ubuntu (or whatever else) are you running?
[/LIST]

---

### Post by freak_lick on 2008-08-30
> **WRDN said:**
> Open the Terminal, and type:

```
sudo fdisk -l
```

The disks and partitions will be listed. Find the device code for the external HDD (it will be /dev/sdaN or /dev/hdaN, where N represents a number).

Now, type:

```
sudo mkdir /media/files
```

If you wish, you can replace "files" with something else.

Now, type:

```
sudo mount /dev/[device] /media/files
```

This will mount the drive.

If it does not work, you could try force- mounting the drive.

```
sudo mount /dev/[device] /media/files -o force
```


The upper-mentioned way is to mount it for only that session, after you restart computer, you will need to mount it again.

If you want to mount it permanently :

In terminal type:

sudo gedit /etc/fstab

then fstab file (file system table) will open and ready for editing.

add

/dev/sdb1 /media/storage ntfs user,exec 0 0

Mine external hdd was on /dev/sdb1 it can be other for you, likr folder i was mounting it to /media/storage .

Wish you all the best

---

### Post by Colo2 on 2008-09-23
thanks all for the help :) all we had to do was plug it in to windows and safely remove hardware

---

