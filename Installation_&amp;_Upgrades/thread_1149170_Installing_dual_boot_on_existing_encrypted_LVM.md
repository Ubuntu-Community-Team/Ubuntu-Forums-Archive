---
title: "Installing dual boot on existing encrypted LVM"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by coviran on 2009-05-04
Hello,

I have a working system with a lvm partition containing various encrypted volumes:

```

fred:~# lvs
  LV           VG   Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  home         fred -wi-ao 124.80G                                      
  root         fred -wi-a-   9.31G                                      
  root_testing fred -wi-ao   9.31G                                      
  swap         fred -wi-ao   4.66G   

```

All the volumes are named intuitively with an existing Debian testing installation on "root_testing" using "home" and "swap".

I would like to install Ubuntu on "root", preserving the other volumes, so that I have a fully encrypted dual boot system sharing the same home directory. Before trying that I would like to ask you for some advice:

- I read lvm is only available with the "Alternate Install CD". Is this still true, even when lvm is already set up?

- Are there dangerous steps of the installation where I do have to be very careful not to overwrite / format / erase ... my existing partitioning / lvm setup?

- Has anyone done this before, are there guides, hints, anything?


kind regards,
covi

---

### Post by mikereed on 2009-05-13
I posted a reply with a similar problem

[http://ubuntuforums.org/showthread.php?p=7270070#post7270070](http://ubuntuforums.org/showthread.php?p=7270070#post7270070)

I don't think this is exactly what you are doing but it may give some strong pointers as to how to proceed.
Good luck.

---

