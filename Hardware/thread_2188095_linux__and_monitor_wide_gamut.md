---
title: "linux  and monitor wide gamut?"
date: 2013-11-15
forum: Hardware
---

### Post by ubunlilluz on 2013-11-15
Hi,
i've like to take the new U2413 of dell. It's a wide gamut monitor and dell provides a sw for controlling the color space for any kind of work (photo editing, dvd, game) so i've the doubt that with Linux i'll not be able to use it, unless it'll work with wine or virtualbox and w7. Anyone is able to work with a wide gamut monitor as 2413, u2410 or any other ones?

---

### Post by ubunlilluz on 2013-11-16
nobody have a wide gamut monitor the process photos?

---

### Post by tgalati4 on 2013-11-16
True, linux does not have decent color management tools, but it can read *.icc profiles that are created in Windows or OS X.

[http://manpages.ubuntu.com/manpages/precise/man1/xcmsdb.1.html](http://manpages.ubuntu.com/manpages/precise/man1/xcmsdb.1.html)

Your best bet is to dual-boot and run Dell's color management tool then copy the *.icc files to the appropriate location.  I don't know if the Dell tools run in Wine, but that might be another option.

What is your workflow that requires controlling color space?

---

