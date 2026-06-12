---
title: "MSI Wind Installation"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by eac101 on 2009-10-12
I am trying to install ubuntu 9.04 on MSI Wind Netbook 123 - it has 160GB HD and Windows XP already installed. Borrowed an external DVD drive to install ubuntu.

The partitions confuse me. There are 3: 1) WINRE 3.91 GB FAT32 EISA Config, 2)OS_Install C: NTFS - 39.07 GB with 30.68 FREE, 3) D: NTFS 106.07 GB with 105.99 FREE

I am not sure what the D: partition is? I would like to install ubuntu on D: and use the whole space and leave Windows on C: with the 39.07 GB - but when I try to install ubuntu it makes another partition and I can drag over but still leaves about 2.5GB on D:

I am not sure why the setup is this way and I do not want to mess anything up by wiping D: clean.

Any help is appreciated - see GIF Screenshot

Ed

---

### Post by SoulSurvivor on 2010-05-03
Are you using Wubi?  that is installing Ubuntu through windows?

EDIT: Drive D: is an NTFS file system.  From what I know you cannot install Ubuntu on an NTFS formatted drive unless you use Wubi (see below).  You must either delete the partition and let Ubuntu create a new one, or using Wubi, install through Windows on Drive D:

Using Wubi creates a virtual file system that is emulated on an NTFS partition so that you don't have to reformat or delete a partition.  However, that can reduce Ubuntu disk performance in a few ways.

---

### Post by frantid on 2010-05-03
I would just try to run the livecd first before attempting the install.  Can you boot off the external drive?  Or if you have a usb thumb drive you can try booting off one of those.

You don't want to touch "winre"  that is your recovery image in case things go wrong with windows.

Wubi is a virtual install, it is like virtual box, or xp mode in win7.  

I would really try a livecd type environment to make sure things are compatible before installing.  Also you probably want the netbook addition.

See this post for a guide:
[http://www.zimbio.com/Ubuntu+Linux/articles/611/Installing+Ubuntu+Netbook+Remix+Jaunty+MSI](http://www.zimbio.com/Ubuntu+Linux/articles/611/Installing+Ubuntu+Netbook+Remix+Jaunty+MSI)

or here:
[http://blog.getasysadmin.com/2009/05/ubuntu-jaunty-on-msi-wind-100.html](http://blog.getasysadmin.com/2009/05/ubuntu-jaunty-on-msi-wind-100.html)

---

