---
title: "Nothing is mounting..."
date: 2009-01-29
forum: Hardware
---

### Post by toasty_ghosty on 2009-01-29
Hello

Due to the recent death of my main computer, I am residing to the Pentium4 I have stored under my bed for awhile..Needless to say after installing Fluxbuntu, nothing seems to want to mount. I tried:

sudo mount /dev/hdc /media/cdrom0/

and nothing.

I have tried to find what my cdrom and flash drive are named, but I cannot seem to find them using dmesg |more but I cannot seem to get it. I would put the print out of that but its very long

Even using the mounting tool gives me this error:

Mounting /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Mount failed

---

### Post by damis648 on 2009-01-29
You need to specify a filesystem, like this:
```
sudo mount -t ext3 /dev/sda1 /media/foo
```

---

### Post by toasty_ghosty on 2009-01-29
> sudo mount -t fat32 /dev/sda1 /mnt/usb/

I cannot seem to find the actaul name for the cd's file type...and how would I figure out what the devices name...

---

### Post by snowpine on 2009-01-30
Give this a try:

```
mkdir ~/.ivman
```

---

### Post by joekwme on 2009-01-30
I'm having the same problem too, though intermittent. Depending on the cd, my cdrom drive is not mounting.  If I put in a music cd, it spins, and then refuses to eject, since it appears to be empty.  The only way to get out the cd is with a paper clip, or just after a reboot.  Sometimes this happens with a dvd or a data cd.

Sometimes the drive works, and other times like now, it doesn't.


thanks

Joe

Intrepid
Asus x83 laptop
4GB ram
intel dual core

---

### Post by damis648 on 2009-01-31
Try this
```
mkdir /media/cdrom
sudo mount -t iso9660 /dev/cdrom /media/cdrom
```

---

### Post by toasty_ghosty on 2009-01-31
> **damis648 said:**
> Try this
```
mkdir /media/cdrom
sudo mount -t iso9660 /dev/cdrom /media/cdrom
```

When I try that I get an error saying that block device /dev/scd0 is write-protected, mounting read only

mount: wrong fs type, bad option, bad superblock on /dev/scd0, missing codepage or helper program, or other error.

---

