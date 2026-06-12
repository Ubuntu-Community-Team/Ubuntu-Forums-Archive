---
title: "TV tuner card"
date: 2005-03-10
forum: Hardware &amp; Laptops
---

### Post by jaguaracer on 2005-03-10
I have a BT878-chipset TV tuner card installed on my system and I having some difficulties getting it to work with Linux.
Under the Device Manager, I see two tabs for BT878 Video and BT878 Audio. Does that mean the drivers are successfully installed?
It does not seem so as neither tvtime nor zapping will display antything.
I have tried installing BTTV 0.9.15 but under the 'building the driver tarballs" ([http://linux.bytesex.org/v4l2/build.html):](http://linux.bytesex.org/v4l2/build.html):) from the following directions:
> mkdir <workdir>
cd <workdir>
tar xzf /path/to/driver-version.tar.gz
cd driver-version
make KDIR=/path/to/kernel/source/tree
make install

I do not know where to build the package.  I tried to set it automagically (just a make command) but to no avail. As well I tried: lib/modules.2.68.1-3-386/build/kernel/source/tree.
```
dancook@dancook:~ $ cd /home/dancook/Desktop/bttv-0.9.15
dancook@dancook:~/Desktop/bttv-0.9.15 $ make
make -C /lib/modules/2.6.8.1-3-386/build SUBDIRS=/home/dancook/Desktop/bttv-0.9.15 modules
make: *** /lib/modules/2.6.8.1-3-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

Any help would be appreciated.
Cheers,
Dan

---

