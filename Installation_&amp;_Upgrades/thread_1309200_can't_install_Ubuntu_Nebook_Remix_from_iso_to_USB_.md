---
title: "can't install Ubuntu Nebook Remix from iso to USB stick"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Kropotkin on 2009-11-01
Hi all,

I would like to install the Ubuntu Netbook Remix on my Eee PC. 

I have downloaded the 9.10 iso file, **ubuntu-9.10-netbook-remix-i386.iso**.

Next, on my Fedora desktop system, I try to install the live OS on a 4GB USB stick using liveusb-creator.

However, every time I try this, liveusb-creator complains that the iso doesn't have a live OS

```
ubuntu-9.10-netbook-remix-i386.iso selected
Verifying filesystem...
Verifying ISO MD5 checksum
ISO MD5 checksum passed
Extracting live image to USB device...
Unable to find LiveOS on ISO
LiveUSB creation failed!
Unable to find LiveOS on ISO
```

I have gone through all the relevant documentation on the Ubuntu site, and there seems to be an inconsistency.

For example, this page [https://help.ubuntu.com/community/Installation/FromImgFiles]("https://help.ubuntu.com/community/Installation/FromImgFiles") says:

> Ubuntu is distributed over the Internet as two types of files: CD image files, called ISOs, and flash image files, called IMGs. To install Ubuntu from flash media, you first need to write the downloaded IMG image to your flash device.


Likewise, this page [https://help.ubuntu.com/community/EeePC/Installation]("https://help.ubuntu.com/community/EeePC/Installation") also refers to an IMG file: > Installation/FromImgFiles documents the process if you download an '.img' flash image file instead of a '.iso' CDROM image file. This is especially helpful for installing Ubuntu Netbook Remix, which as of this writing (2009 September) comes by default as an '.img' file. Yet in my local mirror, for example, [http://ftp.snt.utwente.nl/pub/linux/ubuntu-releases/9.10/]("http://ftp.snt.utwente.nl/pub/linux/ubuntu-releases/9.10/")I don't see an .img file the UNR: 

```
ubuntu-9.10-netbook-remix-i386.iso 23:59 28-10-09 713887744
ubuntu-9.10-netbook-remix-i386.iso.torrent 13:53 29-10-09 27470
ubuntu-9.10-netbook-remix-i386.iso.zsync 13:53 29-10-09 1394511
ubuntu-9.10-netbook-remix-i386.list 23:59 28-10-09 4243
ubuntu-9.10-netbook-remix-i386.manifest
```

For the previous version of the remix, an IMG file was made available: [http://releases.ubuntu.com/jaunty/]("http://releases.ubuntu.com/jaunty/") So where is the IMG file for latest UNR? Without it, how can I install the remix on my Eee PC?

-K

---

### Post by Kropotkin on 2009-11-01
Never mind. liveusb-creator doesn't work for this, but unetbootin does exactly what it is expected.

---

