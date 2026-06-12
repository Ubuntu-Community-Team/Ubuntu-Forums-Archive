---
title: "offline b43-fwcutter not working"
date: 2010-08-23
forum: Hardware
---

### Post by dabockster on 2010-08-23
I've been trying to get my Belkin F5D7000 working using the b43-fwcutter package offline using [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43 - No Internet access"). Howeer, when i get to **sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver**, i get this error:

[B]Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum d41d8cd98f00b204e9800998ecf8427e.
[/B]

A quick reply would be appreciated, as otherwise I have to move a bulky cabinet to get to my modem's ethernet port. ;)

---

### Post by dabockster on 2010-08-24
Anyone got a solution for me?

---

### Post by ubun_two on 2010-08-24
You seem to be using the older version.  Get the drivers here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Depending on your kernel version, you may have to apply patches.  You can find them at the same location.

---

### Post by oleink on 2010-08-24
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/page2.html]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/page2.html")

[http://www.linuxforums.org/forum/ubuntu-help/131548-accessing-internet-3.html]("http://www.linuxforums.org/forum/ubuntu-help/131548-accessing-internet-3.html")


[http://opensuse.us/forum/viewtopic.php?f=3&t=2731]("http://opensuse.us/forum/viewtopic.php?f=3&t=2731")


Hope something in here is helpful.  I have a broadcom card and I hate it haha but if you get it working you'll be pretty comfortable with it

---

### Post by oleink on 2010-08-24
> **dabockster said:**
> Anyone got a solution for me?

Oh wait sorry this is a mistake

---

