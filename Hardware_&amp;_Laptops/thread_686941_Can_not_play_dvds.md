---
title: "Can not play dvds"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by 1adam12gb12 on 2008-02-03
Hi,  New user here. I am trying to get my DVD player working. I am starting to think it is because I can not get this file:
libdvdcss2
 I get this message:
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
 Why is there not a how to on this?

---

### Post by crjackson on 2008-02-03
> **1adam12gb12 said:**
> Hi,  New user here. I am trying to get my DVD player working. I am starting to think it is because I can not get this file:
libdvdcss2
 I get this message:
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
 Why is there not a how to on this?

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

### Post by 1adam12gb12 on 2008-02-04
A thousand thanks! DVD played on VLC but none of the others.

---

### Post by Motorhead Kaze on 2008-02-29
Just to be sure, vid is now playing on all vid players, not just VLC, correct?

---

### Post by 1adam12gb12 on 2008-02-29
no just vlc.

---

