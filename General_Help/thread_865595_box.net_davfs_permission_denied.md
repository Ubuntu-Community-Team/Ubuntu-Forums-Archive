---
title: "box.net davfs permission denied"
date: 2008-07-20
forum: General Help
---

### Post by herschen on 2008-07-20
I mounted my box.net account successfully with the following line:
```
sudo mount -t davfs http://www.box.net/dav /media/box.net
```
I added my username and password to the davfs2/secrets file
and I now mount box.net automatically with the following line in fstab:
[http://www.box.net/dav](http://www.box.net/dav) /media/box.net davfs

But I now realize that I can't write files to my box.net folders without being root.

And when I tried copying files to this volume (as root) I got this error message:
```
cp: cannot create regular file `/media/box.net/SEO.odt': No such file or directory
```

What I would like to do is make my "localhost" directory redirect to the box.net volume, so I can edit my web site from my office and from home, but I doubt this is possible. Thanks for the help.

---

### Post by ilrudie on 2008-07-21
You can try adding the umask=007,gid=46 options to the line in fstab.  Make sure you are a member of the plugdev group (gid=46) but you should be if you can use optical drives and jump/flash drives.

---

### Post by charding on 2011-11-15
> **herschen said:**
> I mounted my box.net account successfully with the following line:
```
sudo mount -t davfs http://www.box.net/dav /media/box.net
```
I added my username and password to the davfs2/secrets file
and I now mount box.net automatically with the following line in fstab:
[http://www.box.net/dav](http://www.box.net/dav) /media/box.net davfs

But I now realize that I can't write files to my box.net folders without being root.

And when I tried copying files to this volume (as root) I got this error message:
```
cp: cannot create regular file `/media/box.net/SEO.odt': No such file or directory
```

What I would like to do is make my "localhost" directory redirect to the box.net volume, so I can edit my web site from my office and from home, but I doubt this is possible. Thanks for the help.

I had the same problem and you need to set 
```
use_locks = 0
```
in your davfs.conf file either in /etc/davfs or in your ~/.davfs file.

---

