---
title: "Zoom 56k USB Modem"
date: 2010-01-07
forum: Hardware
---

### Post by RCepeda on 2010-01-07
Hello everyone, I hope that you guys can help me with this problem. I am running Ubuntu Server Release 9.10, kernel linux 206.1-16-generic, Gnome 2.28.1. I have a amd64 athlon II processor. 
The problem that I am having is that for the longest I have tried to install my usb modem (Zoom 56k model 3095) and I still have not been able to detect it with Gnome-ppp. I have downloaded the driver from this site ([http://www.linuxant.com/drivers/dgc/downloads.php](http://www.linuxant.com/drivers/dgc/downloads.php)) and done everything that is asks me to do to install the proper driver ([dgcmodem-1.11.tar.gz]("http://www.linuxant.com/drivers/dgc/archive/dgcmodem-1.11/dgcmodem-1.11.tar.gz")) as far as I know. I still can not detect my my modem. PLEASE HELP!!! ](*,)
BTW.... The whole purpose for the modem is to install Hylafax server.

---

### Post by gordintoronto on 2010-01-07
If you open Accessories/Terminal and enter the command:
lsusb
it might display the identity of your modem.  That might be:
"USB ID 0803:1300 (Zoom Telephonics USB V.92)"
in which case, you have grabbed the wrong drivers.  I think the Zoom is a "softmodem," also known as a "winmodem."

---

### Post by RCepeda on 2010-01-07
This is my ID 0803:3095. Where can I find out if my modem is a soft or winmodem?

---

### Post by gordintoronto on 2010-01-07
It's a DGC softmodem, so you were in the right area.  However, Ubuntu is based on Debian, so you should have selected "Method B" which uses a .deb

Here's a page you should have gone through:
[http://www.linuxant.com/drivers/dgc/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/dgc/downloads-ubuntu-x86.php)

Oh, oh.  Are you running 64-bit Ubuntu?  My reading is that the drivers are all for 32-bit Linux.

Also, if you run:
uname -r
I think you will find you mis-identified your kernel version.

---

### Post by RCepeda on 2010-01-08
LOL, yeah I did. Just a little fat fingering. Here is my correct version 2.6.31-17-generic. I just got an update today. Do you know of any 64 bit drivers for this modem? or do you know of any modem that will work for my system?
Thanks

---

### Post by gordintoronto on 2010-01-08
If the web site only offers 32-bit drivers, I think it is definitive.

This is kind of funny.  Years ago, I was "the modem master," I could make anything talk to anything using a modem.  There's still a modem on my desk; in 2008 I used it to send a fax.  I don't think I have used it for data in at least three years, which goes back before I used Linux.  I have a working assumption that any "real" modem, attached to a serial port, will work with any version of Linux, without needing an external driver.  But not a winmodem/softmodem.

---

### Post by montana68 on 2011-09-04
I also have the zoom modem 3095 which came with a cd that has all the drivers on it. It also includes Linux, Debian, Ubuntu but for older versions of Ubuntu. I have tried to install the driver but had a problem with it. I am going to read the instructions again and try to reinstall the driver. If you want I can try to post the driver to here. You will probably have to tell me how to post it. I'll also send the directions how to install it.

---

