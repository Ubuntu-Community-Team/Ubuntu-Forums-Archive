---
title: "Help choose version driver"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by xelix_ on 2007-05-25
Hi All
Sorry for bad English
I have installed Ubuntu 6.10 with default linux kernel
I also have modem with chipset pctel (define with help scanmodem). which driver I can choose on [site](http://linmodems.technion.ac.il/pctel-linux/welcome.html)?
Thank you

---

### Post by siglost on 2007-05-25
It appears these drivers are written with RedHat in mind and do not say they work with Ubuntu installation.  I am no expert on the topic, but I would try the one marked *NEW* first :  pctel-0.9.7-9-rht-7.tar.gz.  This is typically going to have the most current support available.

When you download this you will probably need to:

$ tar -xvf pctel-0.9.7-9-rht-7.tar.gz
$ cd pc-tel-0.9.7-9-rht-7
$ ./configure
$ make
$ make install

Anyways, this is how tar.gz normally works.  After it is installed you can rm -rf the pc-tel-0.9.7-9-rht-7 directory and the tar.gz file.

Good luck!

---

### Post by xelix_ on 2007-05-25
but on link "the latest version of Robert's driver" have pctel-0.9.7-9-rht-6_for_Ubuntu-2.6.15-23-386.tgz
althrough linux kernel diffrent with Edgy default (2.6.17-10?)...

---

### Post by siglost on 2007-05-25
I do not see pctel-0.9.7-9-rht-6_for_Ubuntu-2.6.15-23-386.tgz

Where is this?

---

### Post by Sef on 2007-05-25
> I do not see pctel-0.9.7-9-rht-6_for_Ubuntu-2.6.15-23-386.tgz

Where is this?

It's on [Linmodems]("http://linmodems.technion.ac.il/pctel-linux/") page.

---

