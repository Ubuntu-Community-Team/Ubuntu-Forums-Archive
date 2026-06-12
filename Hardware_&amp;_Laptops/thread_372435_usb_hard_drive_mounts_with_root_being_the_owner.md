---
title: "usb hard drive mounts with root being the owner"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by mwillett on 2007-02-28
Does anyone know why that mounting a freshly formatted external usb drive mounts as read only.  I looked at the permissions of the drive and says that root is the owner so I know why I am unable to write to it I just want to change it.

The drive is set to auto mount and mounts to the /media folder
The drive is a fresh format in ext3
The entire /mount directory is owned by root

Is the the proper default behavior?  How can I make this drive writabloe?

---

### Post by prankst3r on 2007-04-19
I have the same question I have a usb harddrive and everytime it is mounted it has root/root ownership.

---

### Post by gohmifune on 2007-04-23
Same here.

---

### Post by forsaken_pariah on 2007-05-05
Try this:

```

[FONT=monospace]sudo chown -R owner:group /media
ls -la /media
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by jerome1232 on 2007-12-13
Ok i was having this problem as well after I reformated a USB harddrive to ext3 using gparted in ubuntu 7.10

what solved the problem for me was


sudo chown root:plugdev /media/disk      (this is my usb drive)

sudo chmod u+rwx /media/disk
sudo chmod g+rwx /media/disk
sudo chmod o-wx /media/disk
sudo chmod o+r /media/disk

now when i run

ls -la /media i get

drwxr-xr-x  8 root root     4096 2007-12-12 21:41 .
drwxr-xr-x 22 root root     4096 2007-12-05 13:20 ..
lrwxrwxrwx  1 root root        6 2007-12-05 02:25 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2007-12-05 02:25 cdrom0
drwxr-xr-x  2 root root     4096 2007-12-05 02:25 cdrom1
**drwxrwxr--  3 root plugdev  4096 2007-12-12 21:41 disk**
lrwxrwxrwx  1 root root        7 2007-12-05 02:25 floppy -> floppy0
drwxr-xr-x  2 root root     4096 2007-12-05 02:25 floppy0
-rw-r--r--  1 root root       47 2007-12-12 21:41 .hal-mtab
-rw-------  1 root root        0 2007-12-12 21:20 .hal-mtab-lock
drwxr-xr-x  2 root root     4096 2007-12-12 17:28 sdb1
drwxrwx---  1 root plugdev 12288 2007-12-12 03:25 WinXP32

as far as i can figure i have now made it that the owner root has read write execute
the group plugdev has read write access and everybody else has read access

i tested unmounting and remounting the drive and it retains these properties, logging as another user who is also in the plugdev group also has read write access so i think this completly resolved the issue

---

