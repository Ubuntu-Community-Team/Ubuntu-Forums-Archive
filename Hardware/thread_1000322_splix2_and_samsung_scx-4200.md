---
title: "splix2 and samsung scx-4200"
date: 2008-12-02
forum: Hardware
---

### Post by suoko on 2008-12-02
i'm trying out splix2 driver from [http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200](http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200) which offers an already alienized x86-32 bit deb.
the printer apparently installs correctly but then doesn't start.
when i try to print a page it says "the printer might not be connected"

is anyoneelse trying this open driver ?

fyi:
when installed it asked configuring postfix (???) and i chose "no configuration" since it has nothing to do with printing.
i'm using the eeePC lean kernel

---

### Post by suoko on 2008-12-05
Bump !
BUG REPORT OPENED

---

### Post by albertz on 2009-01-25
This is probably the best method to use your SCX-4200. I would highly recommend *not* to use the official driver setup (as it really messes around with your system in a way you don't want to know about...) and also not the driver (which seems to be highly buggy). (This is meant as an advise to other readers who search for information how to install their SCX-4200 on Ubuntu or Debian.)

A deb-file (for both x86 and amd64) of splix2 can be found here:
[http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200](http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200)

Don't be confused if you already have the same version (SpliX 2.0.0-rc2) installed on your system (as I had). The deb-file there is a patched SpliX 2.0.0-rc2 (and the patch adds the support for the SCX-4200 and some other printer).

After I installed this deb, I restarted CUPS (just to be sure), restarted gnome-cups-manager (because it cached the available driver list and didn't recognized that I had installed a new one), then selected the new driver with gnome-cups-manager, restarted the printer (deactivated and activated it in gnome-cups-manager) and then I was able to print a test-page and the printer seems to work.

---

### Post by nickpaton on 2009-01-31
New installation of Intrepid 32bit with Samsung scx-4200 usb plugged in during install; first thing I did after the updates was to install the Samsung scx-4200 print driver.

CUPS and its associated dependencies were already installed, scx-4200 was showing in Admin > Printing as a USB device but no driver listed - therefore didn't work! 

Go to [http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200]("http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200")

Scroll to the bottom of the page and downloaded the [splix i386 .deb]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-splix_2.0.0-0.rc2.4lsb3.2_i386.deb").

Click on the deb to install it and wait (and wait...!).  
Eventually a terminal pops up asking how to configure the default mail client (bizarrely).
Type 5 (Leave configuration unchanged).

Installation completes, so close all opened install boxes.

System > Administration > Printing.

Click New printer (ignore the fact that the original scx-4200 is listed there).
Follow through and select the newly added scx-4200.

Finish off by printing a test page.

Finally to tidy up, delete the old scx-4200 listing.

---

### Post by spamoften on 2010-04-06
I found there is no need to install any software to get the printer and scanner working in Ubuntu 9.10

Follow the instructions here:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2075437.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2075437.html)

sudo echo "usb 0x04e8 0x341b" >> /etc/sane.d/xerox_mfp.conf

then run 

sudo xsane

(start xsane from root, scanner device file has wrong permissions)
the scanner will be recognized and works immediately :-)

It seems the samsung printer is compatible with the xerox scanner support built into the Ubuntu 9.10 kernel.

Note:  I had in the past tried to get this scanner and printer working using the Samsung unified driver, and I also tried the splix2 option, both without success.  I've been hacking away at this since Ubuntu 7.10 and now it was so easy, thanks google, and thanks "Linas U" who found this great solution!

Cheers
G

---

