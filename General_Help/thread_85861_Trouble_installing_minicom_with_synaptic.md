---
title: "Trouble installing minicom with synaptic"
date: 2005-11-03
forum: General Help
---

### Post by jlo on 2005-11-03
hello,

When i run synaptic and attempt to install minicom i am getting the following error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/minicom/minicom_2.1-9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/minicom/minicom_2.1-9_i386.deb)
  MD5Sum mismatch

Any thoughts on a workarond?

Thank you in advance.

---

### Post by Xian on 2005-11-03
[QUOTE=jlo]Any thoughts on a workarond?[/QUOTE]
It's a server issue. You can just download the [minicom_2.1-9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/minicom/minicom_2.1-9_i386.deb) package locally and install with dpkg. Place the file in your /home/username directory then issue this command:

```
$ sudo dpkg -i minicom_2.1-9_i386.deb
```

---

### Post by jlo on 2005-11-04
Ok i have tried this and receive the following:

~/Desktop$ sudo dpkg -i minicom_2.1-9_i386.deb
(Reading database ... 61923 files and directories currently installed.)
Unpacking minicom (from minicom_2.1-9_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing minicom_2.1-9_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/man/man1/minicom.1.gz')
Errors were encountered while processing:
 minicom_2.1-9_i386.deb

---

### Post by eddieave1 on 2006-01-20
thanks Xian, it worked for me. I'm new to Linux and I was going nuts trying to install this app. Have a great day.

---

