---
title: "Why can't I mount this hard disk? (Solved)"
date: 2005-11-26
forum: General Help
---

### Post by Kevinator on 2005-11-26
I added a hard disk with the intent of copying some data off of it. It seems to be at /dev/hdc. If I do sudo hdparm /dev/hdc I get... well, something. sudo fdisk -l /dev/hdc seems to confirm that this is what I want. (Side question: is there a nice easy way to check what drives are available?)

So I try to mount it like this:

```

$ mkdir /home/kevin/hdc
$ sudo mount -r -v -t vfat /dev/hdc /home/kevin/hdc
mount: /dev/hdc already mounted or /home/kevin/hdc busy

```

So of course I check whether it is actually mounted, and it doesn't appear to be:

```

$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

```

What am I doing wrong?

---

### Post by aysiu on 2005-11-26
What about when you type in ```
df -h
```?

---

### Post by Kevinator on 2005-11-26
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              88G  1.8G   82G   3% /
tmpfs                1015M     0 1015M   0% /dev/shm
tmpfs                1015M   13M 1002M   2% /lib/modules/2.6.12-10-386/volatile

```

---

### Post by poptones on 2005-11-26
/dev/hda is the *device*, not the filesystem(s) on the device. The filesystems will be in /dev/hda1, /dev/hda2, /dev/hda3 etc.

Post the output you get from sudo fdisk -l /dev/hdc

---

### Post by Kevinator on 2005-11-26
Oh, right. That was a pretty dumb mistake. It worked fine once I added the partition number.

Thanks for the help, guys.

---

