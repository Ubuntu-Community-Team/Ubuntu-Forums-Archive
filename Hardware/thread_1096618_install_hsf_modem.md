---
title: "install hsf modem"
date: 2009-03-15
forum: Hardware
---

### Post by mo.jalilian on 2009-03-15
i install ubuntu but have a very bad problem with my modem.
i can't install this and work with that.
please give me a help step by step to install that.
thanks.

---

### Post by namaku0 on 2009-03-15
What is your modem's chip?

I had one HSF modem with Conexant chip in the past and
I had to compile the driver module manually.

If your modem have same chip you may want to use one
of the DEB package here: 
[http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)

The free version is limited to 14.4 kbps data transfer though...

---

### Post by mo.jalilian on 2009-03-15
and what am i doing after download the file?

---

### Post by namaku0 on 2009-03-15
Unzip it, then double-click on the extracted file (the 
DEB package). The Package Installer's (gdebi) window
will show up and then click "Install Package". It will
ask for your password.

---

### Post by namaku0 on 2009-03-15
BTW, I find it easier to use Gnome PPP to make a dial.
So get it here (for Ubuntu 8.10 / Intrepid Ibex):
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb)

Don't forget to use **/dev/ttySHSF0** as modem device
when configuring Gnome PPP. Below picture is for example
only where you should change it:
[IMG]http://dewo.files.wordpress.com/2008/07/setup-gnome-ppp.png[/IMG]
[SIZE=1]That pic above isn't mine and shamelessly linked against. 
I hope the owner doesn't mind.[/SIZE]\\:D/

---

