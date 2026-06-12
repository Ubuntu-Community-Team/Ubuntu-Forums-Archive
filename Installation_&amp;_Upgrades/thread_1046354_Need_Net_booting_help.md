---
title: "Need Net booting help"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by sidewalkcynic on 2009-01-21
I am stuck in an un-upgradable situation. I was satisfied with 7.04 from a bokstore CD, and when I tried  7.10 I had no sound, so I didn't even bother attempting to upgrade 8.04, and just stayed at 7.04. Any way, I recently, had to reinstall 7.04, because something went haywire with the WiFi; and as I learned, because 7.04 is out of date, I cannot get my applications from the repositories.

I would like to install 8.04 or 8.10 from the Internet some how. All of the [installation tutortial guides]("http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/#more-401") insist on a SYSLINUX MTOOLS apt-get, but it seems my 7.04 can't get it. What do I do?

>  sudo apt-get install syslinux mtools
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package syslinux is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package syslinux has no installation candidate
So I found this [MAKEFILE]("http://lxr.linux.no/syslinux+syslinux-3.50/mtools/") stuff. Do I just plug these lines into the terminal, and that satisfies the requirement?

---

### Post by icanfly0307 on 2009-01-21
If I understood you correctly, you're trying to install Ubuntu over the network right? Try UNetbootin. It helps you install linux from over the internet. Here's the link: [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

