---
title: "apt on cd"
date: 2008-08-13
forum: General Help
---

### Post by mr.farenheit on 2008-08-13
i have apt on cd. i want to be able to save all my codecs and such for my next reinstall. which folders do i add on apt on cd to do so?

---

### Post by Sycron on 2008-08-13
You may try this....[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
Everytime when you'll boot ubuntu from USB it will save your installed programs settings...etc but if you'll install ubuntu to a hdd there would be installed only default programs....

---

### Post by Elfy on 2008-08-13
afaik apton copies only the apt cache, if the codecs have been installed through apt then the downloaded package should be there.

If you have downloaded a deb file and used that then it won't copy it.

---

### Post by Sycron on 2008-08-13
The cache is situated in /var/chache/apt/archives as far as i know. You may save that debs and install all of the with a single command.

For example if you saved them on **/media/disk-1/programs/** you can install them with
```
$ sudo dpkg -i /media/disk-1/programs/*
```

---

### Post by Shazaam on 2008-08-13
Look here.....
[http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html)

---

