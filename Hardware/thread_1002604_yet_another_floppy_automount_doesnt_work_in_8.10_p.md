---
title: "yet another floppy automount doesnt work in 8.10 post"
date: 2008-12-05
forum: Hardware
---

### Post by T_Beermonster on 2008-12-05
Long story short I have added "floppy" to /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
sbp2
fuse
floppy
```

I have added the following to my /etc/fstab
```
/dev/fd0 	/media/floppy0	auto rw,auto,user,exec,sync	0	 0
```

I have created the mountpoint media/floppy0

I have checked that the /dev/fd0 device exists

I still cant mount a floppy.

Using Places -> Removable Media -> Floppy Drive
simply produces some drive access activity and then nothing, no error, no mounting.

Opening computer:/// and trying to access Floppy Drive produces drive access activity and then an error "Unable to mount location" "Can't mount file"

going to the terminal and typing
```
sudo mount -a
```
or
```
sudo mount /media/floppy0
```
produces the error message "mount: you must specify the filesystem type" but this surely is supposed to be what the "auto" filesystem entry in fstab is supposed to deal with.
Using a known vfat disk and entering:
```
sudo mount -t vfat /dev/fd0 /media/floppy0
```
successfully mounts the floppy disk.

What is wrong with the "auto" filesystem option in fstab? Why did they bugger up floppys in the first place?
Obviously it is unsatisfactory to have to invoke root privileges and manually mount/unmout every floppy while specifying a filesystem (which in some cases may not be known in advance).

Is there an actual functioning fix for this because I have followed several googled links and they just don't work.

---

