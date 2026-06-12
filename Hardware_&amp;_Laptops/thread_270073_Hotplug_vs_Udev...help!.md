---
title: "Hotplug vs Udev...help!"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by jtanenbaum on 2006-10-02
I have a piece of specialized tracking equipment that I need to install in Ubuntu.  Unfortunately, the company who manufactures the hardware only developed drivers and install procedures to support Hotplug (and FXload).

The hardware is a [Polhemus Liberty Tracking System.]("http://www.polhemus.com/LIBERTY.htm")  According to the documentation I have, FXload is necessary to install the firmware on the unit.

So I cannot install any version of Hotplug, so far as I know, without first removing Udev, which now handles the device management tasks that Hotplug previously took care of.  Udev, as far as I can tell, is pretty critical to how Ubuntu handles device recognition.  To make my life even more difficuls, the manufacturer of the device has no intention of supporting udev, or of ever updating these drivers.

This leaves me needing to figure out a way to either 

a.)Get hotplug to work in Ubuntu,
or 
b.)figure out how to write rules for Udev for this highly proprietary hardware.
or
c.) incur the wrath and ridicule of my research supervisor by switching to the build that the manufacturers developed the system on...I think redhat 6, or thereabouts.

Any help/advice that anyone can offer would be greatly appreciated.  My experience working with linux is somewhat limited, and I have almost no programming experience.  I went with Ubuntu specifically because I saw that there was a version of hotplug listed among the availible packages online(and because I happened to have a live cd that a friend had given me).  I greatly appreciate any assistance!

---

### Post by jtanenbaum on 2006-10-03
I hate bumping posts on forums but I really need to know if this task is even worth fighting with, or if I need to move to a different linux build.  Has anyone figured out how to use drivers designed for hotplug in udev?  Is there a good rule of thumb for constructing Udev rules?

---

### Post by preuter64 on 2006-11-28
I was just reading your post about Polhemus on Ubuntu.

I got it working for Debian by using a udev rewriting rule. 

But I also have problems on Ubuntu ..

Did you find a solution ?

Thanks for help


  Pat

---

### Post by jtanenbaum on 2006-11-28
I've made some progress.  In the end I opted for a lateral solution....not to use USB.  Instead, I'm using the serial connection for the Polhemus, and a Udev compatible USB to serial adapter for my other serial device...a Parrallax Basic Stamp Micro controller...which is not as finicky as the Polhemeus when it comes to USB firmware. 

I'm glad to hear that someone else is trying to use Polhemus in Linux.  What is your application for it?

---

### Post by omargomez on 2007-03-07
Hi,

Use the following command:

/sbin/fxload -t fx -D /dev/bus/usb/004/003 -s /usr/share/usb/a3load.hex -I /usr/share/usb/PatriotUSB.hex

use lsusb to obtain the  -D param value, ( in my case it was **Bus 004 Device 004: ID 0f44:ef12** )

Cheers,
Omar

---

