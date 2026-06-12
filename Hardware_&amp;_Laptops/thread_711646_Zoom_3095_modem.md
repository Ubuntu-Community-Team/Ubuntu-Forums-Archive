---
title: "Zoom 3095 modem"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by zoomzoomzoom on 2008-02-29
Ok, long story short, got Zoom 3095 usb analog modem off ebay cheap.  It needs 2.6.19 or newer kernel to compile the driver.  My Puppy Linux install that I use regularly has 2.6.18.1 kernel.  Driver module compiled on it wont load without error.  Thinking I have to wait 2 weeks till I get access to broadband again to download latest Puppy with newer kernel.  

However saw on [www.linuxant.com/drivers](www.linuxant.com/drivers) website they have version 1.03 DGC driver for Ubuntu 7.10 precompiled.  I have a Ubuntu 7.10 live cd, so I boot it and check the version of the kernel used by typing "uname -a" in a terminal window (without the quotes).  Get Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux.  Fine I need the 2.6.22.14-generic part.  Now on linuxant site, I click downloads under DGC.  Click "I agree" to their license terms.  Then click Ubuntu Gutsy under Distribution-specific binary packages, look for my kernel which closest is dgcmodem_1.03_k2.6.22_14_generic_ubuntu_i386.deb.zip
and save to desktop.  Extract by left clicking and archiver extracts deb pkg.  Right click and open with pkg installer.   It installs the binary.  Now now open a terminal window and do a "sudo su".  I am in root now.  Type "dgcconfig", it will open and type yes if I want to use this module.  So far, so good.  Now the Gnome dialer doesnt have option of using port /dev/ttyACM0 so we need to type "ln -s /dev/ttyACM0 /dev/modem"   This provides simlink  as the Gnome dialer does offer /dev/modem.   Now open the Gnome dialer  by clicking on System, Administration, Network, click on Modem connection, then fill out your isp info and choose /dev/modem port.  Now click the little box by modem connection and your Zoom 3095 should dial and connect.

---

### Post by zoomzoomzoom on 2008-02-29
Guess little confusing above how I downloaded before I had modem working.  Well I connected first with my other modem (I always keep at least two functional modems around).  You could download on another computer and burn to cd or floppy or to flash card or something.  This isnt a huge download, only like 47kb.

---

