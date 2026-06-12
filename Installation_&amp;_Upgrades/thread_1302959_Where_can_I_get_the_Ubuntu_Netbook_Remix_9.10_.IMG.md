---
title: "Where can I get the Ubuntu Netbook Remix 9.10 .IMG file?!"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by ChrisUK on 2009-10-27
I want to install Ubuntu Netbook Remix 9.10 on my Samsung NC20 and I am trying to follow the instructions here;
[https://wiki.ubuntu.com/UNR/Installation/Easy](https://wiki.ubuntu.com/UNR/Installation/Easy)

It looks like I need a .IMG file to make a bootable USB stick/key but I can't find it anywhere on the Ubuntu Netbook Remix download page - I can only find the .iso file to make a bootable CD?
[http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/)

Any help would be appreciated.

---

### Post by mikewhatever on 2009-10-27
I believe it's now an iso and not an img, and so you'll need another program to transfer the iso to usb. Use usb-creator or unetbootin, both are in the repositories.

---

### Post by ChrisUK on 2009-10-27
> **mikewhatever said:**
> I believe it's now an iso and not an img, and so you'll need another program to transfer the iso to usb. Use usb-creator or unetbootin, both are in the repositories.

Ah ok, thanks. For some reason I thought the .iso wouldn't work on a USB stick and that it was only for CD's?
I'll try it out tomorrow. :)

---

### Post by shaggy999 on 2009-10-28
> **ChrisUK said:**
> Ah ok, thanks. For some reason I thought the .iso wouldn't work on a USB stick and that it was only for CD's?
I'll try it out tomorrow. :)

What you say is true, but there are programs (usb-creator, unetbootin, as mentioned above) that take a bootable linux iso, extract the contents to a usb drive, change some config files, and install a bootloader onto the drive making it work on a flash disk.

---

