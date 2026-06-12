---
title: "Floppy does not exist?"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by kgilkerson on 2006-01-01
I can't mount my Floppy Drive. I kept getting 

"mount: I could not determine the filesystem type, and none was specified"

I edited /etc/fstab, using gedit, [like this thread said to]("http://www.ubuntuforums.org/showthread.php?t=105871&highlight=%22Floppy+Disk%22"), and now I get 

"mount: special device /dev/fd0 does not exist"

But in "computer," under 'places' on the menu bar, there is a floppy1 shown.

What's really weird is that when I changed fstab to read
"/dev/fd0 /media/floppy0 auto,vfat rw,user,noauto 0 0
/dev/fd1 /media/floppy1 auto,vfat rw,user,noauto 0 0"

I opened up "Computer" and there was a floppy2 and a floppy1. Both got the same "does not exist" error message.
Any Ideas? 

Thanks alot,
Ken

---

### Post by Sef on 2006-01-03
Here's how I mounted my floppy: 

 > sudo mkdir /media/floppy
sudo mount /dev/fd0 /media/floppy -t vfat -o umask=000 (Sbasak)

Thread: [http://ubuntuforums.org/showthread.php?t=110132&highlight=floppy]("http://ubuntuforums.org/showthread.php?t=110132&highlight=floppy")

---

### Post by Sef on 2006-01-05
I found this other post which tells how to automount the floppy drive.  That post is listed at the bottom of the page.

This other post of mine tells how I got my floppy drive to automatically boot:


Quote:
There is a bug in Breezy, so often the floppies won't automount. To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install --> sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

I found that bug and fix from this thread: [http://ubuntuforums.org/showthread.php?t=93139&page=2](http://ubuntuforums.org/showthread.php?t=93139&page=2)

---

