---
title: "no permissions to automounted usb harddrive"
date: 2006-12-09
forum: Hardware &amp; Laptops
---

### Post by lewisdw on 2006-12-09
I have a ntfs formatted usb harddrive.  When I plug it in, it's automounted, but I don't have any permissions to it (it's mounted as /media/mp3s).  How do I correct this?

Thanks

---

### Post by Judicata on 2006-12-09
Can you post your /etc/fstab?

---

### Post by lewisdw on 2006-12-09
This is my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               reiserfs notail          0       1
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Thanks again!

---

### Post by samurai1200 on 2006-12-10
I'm a newbie to linux (::ubuntu), but I think i can help a bit.

First, how do you know it's mounted to /media/mp3s?
The fstab you provided shows no evidence of this mount.
For instance, I mount my Windows harddrive like this (in /etc/fstab):

```
/dev/sda1 /windows ntfs nls=utf8,umask=0222 0 0
```

(it's an internal hdd, might be different [and probably IS different] for a USB hdd...)

If I can tell correctly, all you have mounted is your linux partition (sda1 is the structure, sda2 is the swap) and your cdrom is at hda (/media/cdrom0).

When your drive "mounts" is it putting an icon to the drive on your desktop?

P.s. I just turned on my seagate external usb hdd, but it made no changes to my fstab. This means USB devices are handled elsewhere (i mean... fstab's comments DO say its for static file systems...)

[edit:] couldn't you just...
```
sudo chmod 777 /media/mp3s/*
```
(**DO NOT** try this until it has been verified by someone with more experience than me. ALSO, you'll probably want to use chmod 755 for safety, or 744/444 for extra safety.)

---

### Post by lewisdw on 2006-12-10
samuari1200 -

I know it's mounted at /media/MP3s because it shows up in my /etc/mtab (see the last line):
```

/dev/sda1 / reiserfs rw,notail 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdh1 /media/MP3s ntfs rw,noexec,nosuid,nodev,sync 0 0

```

That line disappears when I unplug the drive.  Also, /media/MP3s appears and disappears with the drive.

I did try to change the permissions on the directory, but it didn't allow it:

```

$ sudo chmod 777 /media/MP3s
chmod: changing permissions of `/media/MP3s': Read-only file system

$ sudo chmod 777 /media/MP3s/*
chmod: cannot access `/media/MP3s/*': No such file or directory

```

I'm probably missing something very simple, I just don't know what. ](*,) 

Thanks

---

### Post by yuanfangcan on 2006-12-10
We have Red hat linux box in our lab. By default the linux will automount the NTFS hard drive read only. I heard that even some package can help the linux to write on the NTFS hard drive, but it is not very safe. Maybe I am wrong. 

We use the NTFS to backup. So what I have done is to convert NTFS to EXT3 using mkfs.   then unplug it, then plug it, it will automount under /media/xxx.  then chmod 777 XXX,  then you can read and write on it.

---

### Post by lewisdw on 2006-12-12
> **yuanfangcan said:**
> We have Red hat linux box in our lab. By default the linux will automount the NTFS hard drive read only. I heard that even some package can help the linux to write on the NTFS hard drive, but it is not very safe. Maybe I am wrong. 

We use the NTFS to backup. So what I have done is to convert NTFS to EXT3 using mkfs.   then unplug it, then plug it, it will automount under /media/xxx.  then chmod 777 XXX,  then you can read and write on it.

I'd rather not convert to another file system on the external drive (makes it hard to use on non-linux systems).  But if that's the only way to use it, can you explain how to do this?

Thanks

---

### Post by yuanfangcan on 2006-12-24
[QUOTE=lcan you explain how to do this?

[/QUOTE]

You need to umount the NTFS external hard drive at first. Then format it. 
To format it, just one command:  mkfs -t ext3 /ext/hd*. This step is pretty fast. It is in 10 min for my 500G drive.

---

### Post by etank on 2006-12-28
If the drive is already NTFS you could install ntfs-3g and mount it in read / write mode. That is what I just did with my SimpleTech usb drive.

---

