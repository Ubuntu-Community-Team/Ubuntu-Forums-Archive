---
title: "password usb"
date: 2008-07-22
forum: General Help
---

### Post by pavel989 on 2008-07-22
is there a way to encrypt/password a usb pen drive such every operating system has to deal with it? or does encryption do that for everything?

---

### Post by conehead77 on 2008-07-22
Im not sure if i understand your question correct.
You can encrypt a USB stick with [http://www.truecrypt.org/](http://www.truecrypt.org/) for example. You need to install truecrypt on every computer/operating system from which you want to access the data.
Unfortunately, truecrypt isnt in the Ubuntu repositories, so you need to download it from the website and then install. There are several versions for Windows, Mac and some Linux distributions available.
There may be other encryption programs, but i only know of truecrypt.

Hope this helps

---

### Post by bodhi.zazen on 2008-07-22
There are several encryption algorithms ...

If you want a gui and cross platform compatibility, +1 truecrypt. The only potential problem is you will need admin privileges on all machines.

You can use gpg, LUKS, and bcrypt (bcrypt is cross platform, no admin rights required, but command line only).

[http://bcrypt.sourceforge.net/](http://bcrypt.sourceforge.net/)

By defintion you can not decrypt an encrypted partition / flash drive without the proper software and password (or one BIG computer and some free time).

---

