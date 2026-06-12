---
title: "Cannot copy onto usb key (No space left on device)"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by mabster on 2006-01-17
I just plugged my usb key (Mambo-X MP3 player specifically) and it didn't work as I expected.  It appeared in gnome as a new device and I could see the files inside, etc. but not copy to it.  I tried both from Nautilus and the shell.  Here's what I get:

```
root@ubuntu:/media/usbdisk/New# cp /home/user/*.mp3 .
cp: writing `./track.mp3': No space left on device
```

I definitely have enough space on the drive (I deleted a whole bunch of files off just beforehand via Nautilus).  Note that I logged in as root because I've had problems with some other devices being read-only in my user-mode.  Here's the mount:

```
root@ubuntu:/media/hdc5/temp# mount
<snip>
/dev/sda1 on /media/usbdisk type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)
```

Any idea why this would happen?

---

### Post by Qrk on 2006-01-17
Show the hidden files on the device. When you deleted the files they went to a trash folder; delete that trash folder and you should be good to go.

---

### Post by toorima on 2006-01-17
Check hidden files, you might have a .trash on the usb key

---

### Post by mabster on 2006-01-18
Thanks Guys!

I had a funny feeling it was something like this on the way to work this morning.  When I switched on my mp3 player, all the tracks I had deleted played before all the other tracks too ;)

---

