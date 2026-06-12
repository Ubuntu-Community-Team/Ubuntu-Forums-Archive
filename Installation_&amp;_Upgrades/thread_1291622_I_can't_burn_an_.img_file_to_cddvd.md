---
title: "I can't burn an .img file to cd/dvd"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by hanscc on 2009-10-14
Hi guys..

is any one can show me how to burn ubuntu-9.04-netbook-remix-i386.img file?

---

### Post by coldReactive on 2009-10-14
The IMG File is meant for burning to a USB Pen/Flash Drive.

Get one of these: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD), install it to your netbook,

then in the terminal when it boots to terminal, do **sudo apt-get install ubuntu-netbook-remix**.

---

### Post by wilee-nilee on 2009-10-15
[quote=hanscc;8106521]Hi guys..

is any one can show me how to burn ubuntu-9.04-netbook-remix-i386.img file?[/QUOTE

So you might share with us 1st are you trying to install in a netbook or a pc or a laptop with a cd player or can you install with thumb drive.

---

### Post by earthpigg on 2009-10-15
.img is intended for a USB stick.

easiest method, will work on any UNIX or Linux distribution, and i think OS X:

[http://wiki.archlinux.org/index.php/Beginners_Guide#USB_stick](http://wiki.archlinux.org/index.php/Beginners_Guide#USB_stick)
> ***Warning***: This will irrevocably destroy all data on your USB stick!

_***UNIX Method:***_

Insert an empty or expendable USB stick, determine its path, and write the .img to the USB stick with the /bin/dd program:

```
dd if=/path/to/FILENAME.img of=/dev/sdx
```

where if= is the path to the img file and of= is your USB device. Make sure to use /dev/sdx and not /dev/sdx1. 

the easiest way to 'determine its path' is to type 'mount' in a terminal and read the output.

---

