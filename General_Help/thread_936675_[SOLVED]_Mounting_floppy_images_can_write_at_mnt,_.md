---
title: "[SOLVED] Mounting floppy images: can write at /mnt, not in /media"
date: 2008-10-03
forum: General Help
---

### Post by BrentNewland on 2008-10-03
I'm working on a project that requires me to mount and unmount floppy and ISO images, so I found a script that does it for me (in Nautilus):
[http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/](http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/)
I did modify it (removed the FS declaration so I could do different file types).

I have a problem with it though: When I have it set to mount at /mnt (folder I created owned by root with RWXR-XR-X permissions) I can access the image just fine. When I have it mount at /Media/Virtual (folder I created owned by myself with same permissions), all the files inside that folder (contents of the image) are owned by root:root and I can't do anything with it.

Any ideas?

```
#!/bin/bash
#
for I in `echo $*`
do
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo mount -o loop,user $I /mnt
  done
done
exit0
```

---

### Post by BrentNewland on 2008-10-03
Just figured out that I can't do anything in either mount point, but the lock icon appears on all files in the /media/virtual mount, not the /mnt mount.

*edit* After a bit more searching, I've found that linux can't mount ISO files as read-write - although I **swear** doing this exact thing a couple months ago, mounting a disk image, adding some files, and saving it again without any special tools and all from the command line.

*edit2* Now I **know** that I'm not crazy! From [wikipedia]("http://en.wikipedia.org/wiki/Loop_device"): 
> 
After mounting a file containing a filesystem, the files within the filesystem can be accessed through the usual filesystem interface of the operating system, without any need for special functionality, such as **reading and writing to ISO images**, in applications.


So why isn't it working?

*edit3* I added "rw" to the options and changed back to the media/virtual mount point, my script now looks like this:

```

#!/bin/bash
#
for I in `echo $*`
do
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo mount -o rw,loop,user $I /media/Virtual
  done
done
exit0

```

I can make directories in it now with sudo, but it's all blocked off to me in Nautilus (everything owned by root and locked).

*edit4* Fixed it, here's how the script turned out:
```

#!/bin/bash
#
for I in `echo $*`
do
filetype=$(file "$I")
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo umount /media/Virtual
sudo mount -v -o rw,loop,uid=$UID $I /media/Virtual && gdialog --title "Mounting Success" --msgbox "File Info: $filetype \n\nFile was mounted successfully:)" 600 400 || gdialog --title "Mounting Failure" --msgbox "File Info: $filetype \n\nFile failed to mount. Please verify file integrity and compatibility." 600 400
  done
done
exit0

```

Had to specify the UID(UID is current user's, dynamically). This will work for floppy disk image files, ISO files, and probably bin/cue, NRG, and MDF (and some others). Goes in ~/.gnome2/nautilus-scripts as MountImage and chmodded 777 (must visit folder once in nautilus for it to work); must also create /media/Virtual. Will automatically unmount anything at /media/Virtual and mount the selected file, returns success or fail message.

---

