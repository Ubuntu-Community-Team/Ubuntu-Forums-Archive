---
title: "Harddrive read only?"
date: 2009-01-04
forum: Hardware
---

### Post by eats7 on 2009-01-04
Hello, I have ubuntu 8.10 installed on my ps3, and ever since upgrading, i cant seem to copy anything to an external harddrive.When I copy something to it, it says : Error while copying to "Disk" The destination is read-only. it is formatted in fat32, it's a 320gig 3.5" in a usb enclosure. I have remounted it and tried changing permissions but to no avail. Psubuntu is dead, so i don't bother posting there, as it also seems to be more a software issue as it was working before (on 7.10), All help is appreciated.

---

### Post by taurus on 2009-01-04
Is the external drive /dev/sdb1?  You could try something like

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by eats7 on 2009-01-04
its actually /media/320IDE

so would i just do 320IDE instead of sdb1?

---

### Post by uidb4056 on 2009-01-04
Yes. But you can skip the first command suggested because the folder has been created yet.

---

### Post by eats7 on 2009-01-04
okay i changed some things... it says this:

```
tyler@ps3ubuntu:~$ sudo mount -t vfat /dev/sda1 /media/320IDE -o umask=000
mount: /dev/sda1 already mounted or /media/320IDE busy
mount: according to mtab, /dev/sda1 is already mounted on /media/320IDE

```

after this i tried it, and it still says the drive is read only... I've changed the permissions and everything, but its like it doesnt know i changed them or something..

---

### Post by taurus on 2009-01-04
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by eats7 on 2009-01-04
tyler@ps3ubuntu:~$ sudo fdisk -l
The number of cylinders for this disk is set to 38913.
This is larger than 1024, and may cause problems with:
1) software that runs at boot time (e.g., LILO)
2) booting and partitioning software form other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Disk /dev/sda: 255 heads, 63 sectors, 38913 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Boot   Begin    Start      End   Blocks   Id  System
/dev/sda1            1        1    38913312568641    b  Unknown
The number of cylinders for this disk is set to 38913.
This is larger than 1024, and may cause problems with:
1) software that runs at boot time (e.g., LILO)
2) booting and partitioning software form other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Disk /dev/sde: 255 heads, 63 sectors, 38913 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Boot   Begin    Start      End   Blocks   Id  System
/dev/sde1   *        1        1    38912312560608+   c  Unknown

---

### Post by uidb4056 on 2009-01-06
> **eats7 said:**
> okay i changed some things... it says this:

```
tyler@ps3ubuntu:~$ sudo mount -t vfat /dev/sda1 /media/320IDE -o umask=000
mount: /dev/sda1 already mounted or /media/320IDE busy
mount: according to mtab, /dev/sda1 is already mounted on /media/320IDE

```after this i tried it, and it still says the drive is read only... I've changed the permissions and everything, but its like it doesnt know i changed them or something..

Can you post the output of:

cat /etc/fstab

This can give information about the message you get when try to mount.

---

