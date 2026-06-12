---
title: "cannot install new programs"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by dirtymotha21 on 2009-09-14
hi i just installed ubuntu on my computer, im having a hell of a time installing new programs , i tried to install limewire, i forgot what the message said but somethin about permission to install it, tried to install a few other things n it wont let me anyone else have this problem? also it ubuntu wont let me go into my "lost and found" folder saying i dont have permission to do so, i was tryin to see if im the admin for my comp but it seems that this "root" guy is haha, help?

---

### Post by cariboo on 2009-09-14
You should have a look at Add/Remove Applications at the bottom of the Applications menu. It is not the same as Add/Remove Programs in Windows, it is one of the preferred methods of installing programs. Another is System-->Administration-->Synaptic Package Manager.

There is a Linux version of Limewire called Frostwire, you may have better success installing that. Windows programs will not install on Ubuntu, as they are totally different file systems.

To access anything outside your home directory you need to be root. Root is disabled on an Ubuntu installation, so we use sudo to give ourselves root privileges when needed. For instance if you wanted to update the package database in a terminal you would type:

```
sudo apt-get update
```

If you wanted to access Lost+Found from the file manager you would press Alt-F2 and type:

```
gksudo nautilus
```

the above command will open the file manager as root and allow to to copy, move, delete and more, to files that aren't in your home directory.

I would suggest a good palce to start, is to go 
[here]("http://ubuntuforums.org/showthread.php?t=1052065"), and download and read the Ubuntu Pocket Guide.

---

