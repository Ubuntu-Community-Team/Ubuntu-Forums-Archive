---
title: "How do I install a .patch file? (for my wireless NIC)"
date: 2008-11-11
forum: General Help
---

### Post by Panarchy on 2008-11-11
Hi

Wondering how to install a .patch file.

I'm using the latest version of ubuntu (8.10).

Here's the .patch: [http://patches.aircrack-ng.org/rtl8187_2.6.27.patch](http://patches.aircrack-ng.org/rtl8187_2.6.27.patch)

Please tell me how to apply/install it.

Thanks in advance,

Panarchy

---

### Post by Crafty Kisses on 2008-11-12
I've installed a similar patch, and I'm pretty sure it would go like this:
```
cd /home/user/Desktop/patch
./configure
make && make install
```

---

### Post by bodhi.zazen on 2008-11-12
See these links :

[http://www.ubuntuforums.org/showthread.php?&t=324672](http://www.ubuntuforums.org/showthread.php?&t=324672)

	[http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

	[http://linux.die.net/man/1/patch](http://linux.die.net/man/1/patch)

---

### Post by iponeverything on 2008-11-12
It's not quite that easy. 

The process is going to be somewhat like what you will find here:

[http://ubuntuforums.org/showthread.php?p=6136347](http://ubuntuforums.org/showthread.php?p=6136347)

Take a look at:

[http://www.cpqlinux.com/patch.html](http://www.cpqlinux.com/patch.html) 

for applying the patch.

It will be a good exercise for you.

---

### Post by Panarchy on 2008-11-12
Tried 
```

sudo patch -p0 rtl8187_2.6.27.patch
sudo patch -p1 rtl8187_2.6.27.patch
```

What am I doing wrong?

Panarchy

---

### Post by iponeverything on 2008-11-12
apt-get the kernel source for 2.6.27 and build-essential  

the rt driver that needs to be patched will under the kernel source tree.
patch it, rebuild the module and install it.


BTW - It not trivial, but its not super hard either.

Please look at:

[http://ubuntuforums.org/showthread.php?t=903124](http://ubuntuforums.org/showthread.php?t=903124)

---

