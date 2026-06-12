---
title: "install on old Omnibook XE3 GF"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by cyrano on 2005-10-19
Hi to all

I am trying to install ubuntu 5.10 on a old Hp Omnibook xe3gf and while installing I recive an error by debootstrap which stop the install.

I tried with "noapic nolapic" kernel append, but nothing ... it seems ubuntu doesn't like the small hp partition (100 mb at the start of the disk) ... but I can't know why.

I told to the install program that it can ignore this partition, ubuntu don't wont to install.

Thanks to all, best regards ;-)

P.S.
I have installed on the same laptop: Gentoo, debian, mandrake & fedora in the past, but ubuntu never want to get up and run :-(((

---

### Post by taygan on 2005-10-19
search on the forums for debootstrap.. Lots of folks are having this problem.  could be a bad cd, check the md5sum

md5sum (name of iso.iso), compare it to the md5sum from the archives.

burn the cd at a slower speed.

check md5sums of all the files. (open cd and you'll find the md5sum file)

If you're using windows, try the md5summer program.

If all those check out and you still ahve problems, try alt-f3 (f2? f4?) (2 and 4 give you the error messages if I remember correctly)

and try  hdpam -d 1 /dev/sda (assuming your cd drive is at /dev/sda) this will ENABLE DMA, which should make the drive work correctly.

---

### Post by cyrano on 2005-10-20
Yes It was a strange thing. The same cd that don't want to installa on the notebook, get up and run on a normal pc ... cdr are a strange world ;-)

Now I have ubuntu installed, using a cd burned at 4x with the same iso image.

Thanks for the answer

---

