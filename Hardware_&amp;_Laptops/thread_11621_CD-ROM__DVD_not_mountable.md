---
title: "CD-ROM / DVD not mountable?"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by franklin82 on 2005-01-18
Hello everybody,

I have a problem with my CD-ROM Writer and DVD player, I can't mount both of them.
Here a few pieces form my configuration files and kernel messages.

dmesg|less
...
hdc: PLEXTOR CD-R PX-W1610A, ATAPI CD/DVD drive
hdd: Pioneer DVD-ROM ATAPIModel DVD-106S 011, ATAPI CD/DVD-ROM drive
...

less /etc/fstab
...
/dev/hdc           /media/cdrom0        udf,iso9660     ro,user,noauto        0            0
/dev/hdd           /media/cdrom0        udf,iso9660     ro,user,noauto        0            0
...

less /etc/udev/udev.rules
....
# /dev/cdrom symlink
#BUS="ide", KERNEL="hd[a-z]", PROGRAM="/etc/udev/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2}"
BUS="ide", KERNEL="hd[a-z]", SYMLINK"cdrom dvd"


# permissions for IDE CD devices
BUS="ide", KERNEL="*[!0-9]", PROGRAM="/bin/cat /proc/ide/%k/media", RESULT="cdrom*", NAME="%k", MODE="0660", GROUP="cdrom"
...

Weird error?
...$sudo mount -t iso9660 /dev/hdc /media/cdrom0
mount: special device /dev/hdc does not exist

..$sudo mount -t iso9660 /media/cdrom0 /dev/hdc
mount: mount point /dev/hdc does not exist

I have also tried several "mount" things for CD-ROM's from the Hello everybody,

I have a problem with my CD-ROM Writer and DVD player, I can't mount both of them.
Here a few pieces form my configuration files and kernel messages.

dmesg|less
...
hdc: PLEXTOR CD-R PX-W1610A, ATAPI CD/DVD drive
hdd: Pioneer DVD-ROM ATAPIModel DVD-106S 011, ATAPI CD/DVD-ROM drive
...

less /etc/fstab
...
/dev/hdc           /media/cdrom0        udf,iso9660     ro,user,noauto        0            0
/dev/hdd           /media/cdrom0        udf,iso9660     ro,user,noauto        0            0
...

less /etc/udev/udev.rules
....
# /dev/cdrom symlink
#BUS="ide", KERNEL="hd[a-z]", PROGRAM="/etc/udev/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2}"
BUS="ide", KERNEL="hd[a-z]", SYMLINK"cdrom dvd"


# permissions for IDE CD devices
BUS="ide", KERNEL="*[!0-9]", PROGRAM="/bin/cat /proc/ide/%k/media", RESULT="cdrom*", NAME="%k", MODE="0660", GROUP="cdrom"
...

Weird error?
...$sudo mount -t iso9660 /dev/hdc /media/cdrom0
mount: special device /dev/hdc does not exist

..$sudo mount -t iso9660 /media/cdrom0 /dev/hdc
mount: mount point /dev/hdc does not exist

Adding extra repositories and installing several program's etc, that worked just fine.  ([http://ubuntuguide.org/](http://ubuntuguide.org/))

I have installed dvd playing support: [http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)
I have added a symlink for the /dev/dvd: [http://ubuntuguide.org/#symbolicdevdvd](http://ubuntuguide.org/#symbolicdevdvd)

Mounting or unmounting does not work..
[http://ubuntuguide.org/#mountunmountcddvdromunhide](http://ubuntuguide.org/#mountunmountcddvdromunhide)

I must be missing something here, this is also the first Linux distribution with the 2.6 kernel that I'am using. 
Maybe somethings changed while I was playing with Slackware 10.0 with 2.4 kernels?

Frank

---

### Post by SWAT on 2005-05-14
I also have a Pioneer DVD drive (with dual-layer burn capabilities) and I have EXACTLY the same problem. Windows recogizes/uses everything without a problem. What's going on here? 
The DVD drive is connect on my IDE channel and on the same IDE channel is my other CD/DVD drive connected (Samsung) and that works/mounts fine. Help?

---

