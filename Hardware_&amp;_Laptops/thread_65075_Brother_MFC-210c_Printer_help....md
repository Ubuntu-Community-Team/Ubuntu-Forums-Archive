---
title: "Brother MFC-210c Printer help..."
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by nosmada on 2005-09-12
I am new to ubuntu and linux also and I am trying to get my printer working. I've searched around and haven't quite found any posts that really help. It is a Brother MFC-210c and I have gone to [http://solutions.brother.com/linux/](http://solutions.brother.com/linux/) and read through all that I could find there and have followed there instructions. When I enter the commands in the terminal I get this:

```
nosmada@NosmadaLinux-00:/$ sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb
Password:
(Reading database ... 61750 files and directories currently installed.)
Preparing to replace mfc210clpr 1.0.2-1 (using mfc210clpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc210clpr ...
Setting up mfc210clpr (1.0.2-1) ...
ln: `/usr/lib/libbrcompij2.so.1.0': File exists
ln: `/usr/lib/libbrcompij2.so.1': File exists
ln: `/usr/lib/libbrcompij2.so': File exists

nosmada@NosmadaLinux-00:/$ sudo dpkg -i --force-all cupswrappermfc210c_1.0.0-1_i386.deb
(Reading database ... 61750 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using cupswrappermfc210c_1.0.0-1_i386.deb) ...
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...

 ****** ERROR: csh is required. ******
``` 

If anyone can help on what that error message means that would be great or if they know of another way to install it. Thanks in advance.

---

