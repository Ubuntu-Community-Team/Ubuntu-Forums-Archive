---
title: "Scanner Driver Installation Instructions"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by Robbyx on 2006-12-19
I  have found a driver for my  pixma mp750 scanner  Being new to Linux I am having a problem understanding the installation instructions. I am using Ubuntu Edgy 6.10.

Can someone please tell me how to carry out the two instructions below. I have dowloaded the actual driver but do not know how to integrate it into Ub.

[I]$ make
$ sudo make install

Test
====

$ sudo make test


Usage
=====

The image acquisition tool is called pixma_scan and must be run as root.  You
will get a short help message if you run it without any argument.


Example
=======

$ sudo pixma_scan -r 150 -x 60 -y 10 -w 800 -h 580 -o test.pnm[/I]

Robin

---

### Post by MeduZa on 2006-12-26
I have the same problem with my pixma MP530 the printer don't works fine with the driver that comes with ubuntu and the scanner is detected but not by xsane

Some body can help us? :confused:

---

### Post by Robbyx on 2006-12-26
I have two sources for the scanner drivers:

1. [http://www.hamrick.com/vsm.html](http://www.hamrick.com/vsm.html)

2. [http://pixma.schewe.com/](http://pixma.schewe.com/)

They are different drivers but  I do not know how to install them.

Any help out there?

Robin

---

