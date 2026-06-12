---
title: "Camera unmounting woes"
date: 2008-11-13
forum: Hardware
---

### Post by vaporjourney on 2008-11-13
I've searched thru the archives trying to find a solution to my problem.  The problem is the sporadic way Ubuntu seems to allow me to unmount my Nikon d40.  Sometimes it will allow me to right-click the desktop icon and unmount it.  lately though, when I try to do this, nothing happens.  The last time, I was able to unmount it using the umount command.  Today though I'm getting this message:

hearsay@hearsay-desktop:~$ umount /media/nikon d40
umount: /media/nikon is not mounted (according to mtab)

when I check the mounted devices via 'mount' command, i get this:

hearsay@hearsay-desktop:~$ umount /media/nikon d40
umount: /media/nikon is not mounted (according to mtab)

so I'm assuming that the camera is actually mounted in reality?  can anyone help me unmount this since I can't force it to unmount in the terminal?  Also...what can I do so that in the future I won't have these annoyances?

---

### Post by taurus on 2008-11-13
You need to put the mount point in quotes if there is a space between words.

```
sudo umount /media/"nikon d40"
```
Assuming "nikon d40" is the right mount point.

```
df -h
```

---

### Post by vaporjourney on 2008-11-13
Now I'm seeing an i/o error when I do the 'df -h' command.  hm.  doesn't say this when I use the 'mount' command:::

hearsay@hearsay-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      6.5G  3.5G  2.7G  57% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   52K  506M   1% /dev
devshm                506M  176K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon      6.5G  3.5G  2.7G  57% /home/hearsay/.gvfs
/dev/sda1             233G  157G   76G  68% /media/Video Capture
df: `/media/NIKON D40': Input/output error

---

### Post by taurus on 2008-11-13
Looks like it's /media/NIKON D40, not /media/nikon d40.  Upper case letters are not the same as lower case letters in Unix/Linux since Unix/Linux is case sensitive.

```
sudo umount /media/"NIKON D40"
```

---

### Post by vaporjourney on 2008-11-13
after rebooting, now it isn't showing the camera as mounted, which is fine.

Still this begs the question:  is there anyway to ensure that I can unmount via right-clicking every time without having to enter the terminal?

---

### Post by taurus on 2008-11-13
You should be able to unmount it with a mouse if it's automounted when you plug it in.

---

### Post by vaporjourney on 2008-11-13
exactly.  and for some reason it won't allow me to do this, although automounting has never been an issue...

---

