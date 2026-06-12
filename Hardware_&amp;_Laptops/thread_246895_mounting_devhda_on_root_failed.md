---
title: "mounting /dev/hda on /root failed:"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by Papa-san on 2006-08-29
Everything was working OK last night. I shut down as usual, and it went as usual. When I booted up this morning, I got nowhere...
```

Uncompressing Linux... Ok Booting the kernel
mount: Mounting /root/sda1 /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys /root/sys failed: No such file or directory
mount: Mounting /pro /root/pro failed: No such file or directory
Target filesystem doesn't have /sbin/init


Busybox v1.01 (debian 1:1.01-4ubuntu3) Built-in shell (ash)

Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off
#
```I have a Dell Lattitude C610.
Edit:
I searched on some of the keywords here, but didn't find anything that worked. I found the exact same code, but his issue was fixed in a way that had no effect on my system?!?

Wondering if a Moderator might think it a good idea to move this thread to the beginner's forum? (Seeing as how I am a nOOb)

---

### Post by moimies on 2006-08-30
I had the same problem yesterday and I got figured it out. [http://ubuntuforums.org/showpost.php?p=1305024&postcount=2]("http://ubuntuforums.org/showpost.php?p=1305024&postcount=2") There was the solution. Boot with live linux (I used knoppix). Then, mount your root partition somewhere, like in /mnt. It must be mounted with option "rw", read/write. Then just download the newest version of udev and install it:
```

chroot /mnt
wget http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_079-0ubuntu34_i386.deb
dpkg -i udev_079-0ubuntu34_i386.deb

```
(You can remove that .deb-package if you want.)

That should do the trick.

---

### Post by Papa-san on 2006-08-30
I mount the root with that command?
```
chroot /mnt
```

Because going to my file-system didn't show anything that would mount. (I tried it through terminal, and also looked in the graphical interface., and it didn't do anything.)
 I also tried this:
```

sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev 
```
It said all my versions were the newest available, and wouldn't be changed.

---

### Post by Papa-san on 2006-08-30
I managed to get the Dapper to go live, but it didn't seem to help:
```
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ chroot /mnt
chroot: cannot change root directory to /mnt: Operation not permitted
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$
```
I'm going to try the other suggestions again in this live session and see if it makes any difference.

---

### Post by moimies on 2006-09-01
> **Papa-san said:**
> 
 I also tried this:
```

sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev 
```
It said all my versions were the newest available, and wouldn't be changed.
Try this then:
```

sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install --reinstall udev
```

---

### Post by thathatman on 2006-10-19
This worked perfectly for me!

> **moimies said:**
> I had the same problem yesterday and I got figured it out. [http://ubuntuforums.org/showpost.php?p=1305024&postcount=2]("http://ubuntuforums.org/showpost.php?p=1305024&postcount=2") There was the solution. Boot with live linux (I used knoppix). Then, mount your root partition somewhere, like in /mnt. It must be mounted with option "rw", read/write. Then just download the newest version of udev and install it:
```

chroot /mnt
wget http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_079-0ubuntu34_i386.deb
dpkg -i udev_079-0ubuntu34_i386.deb

```
(You can remove that .deb-package if you want.)

That should do the trick.

---

