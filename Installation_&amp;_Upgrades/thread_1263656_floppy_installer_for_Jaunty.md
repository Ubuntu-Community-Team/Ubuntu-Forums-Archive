---
title: "floppy installer for Jaunty"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by sosabe on 2009-09-11
Hi, everybody.

The fact that Ubuntu floppy installers do not exist is well-known. If we cannot use the cd/dvd installaton or pxeboot installation, we have to use loadlin or grub for the PC on which other Linux distribution or other Ubuntu version is installed. These methods are pretty difficult.  

However, I modified the Fedora floppy installer ([http://www.thisiscool.com/fcfloppy.htm](http://www.thisiscool.com/fcfloppy.htm)) and made  an Floppy installer for Ubuntu Jaunty(i386 desktop version). When you use this installer, you can boot Ubuntu installer and will install Ubuntu via network.  I uploaded it on my homepage([http://sarl-tokyo.com/](http://sarl-tokyo.com/))  which are japanese pages(sorry). However the installer can be got by a ftp client or a web browser directly.  The url of the installer is

[http://sarl-tokyo.com/files/Ubuntu/floppy-installer/Jaunty/ubuntu-jaunty-fi.tar.gz](http://sarl-tokyo.com/files/Ubuntu/floppy-installer/Jaunty/ubuntu-jaunty-fi.tar.gz)  

If you use this installer, you have to make the first floppy disk writable. If your PC is too old to support ACPI and the installer does not work well, then you may succeed in installation by modifing the ubnutu.bat file in the first floppy disk as follows. 

loadlin linux initrd=initrd.gz
->
loadlin linux noacpi acpi=off initrd=initrd.gz

I am sorry for bad english writing.  Enjoy.

---

