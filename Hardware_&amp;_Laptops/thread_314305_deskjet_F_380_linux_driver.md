---
title: "deskjet F 380 linux driver"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by MayItBe on 2006-12-07
Hi,

I am trying to install a Deskjet F 380 printer on Ubuntu. I only have the Windows and Mac drivers. By looking for linux drivers I mananges to find and download hplip-1.6.10.run from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/). I copied it to my usb flash disk and from there to the computer hooked up to the printer (this computer is not yet connected to the Internet).
I launched the .run file and the program said it could not install because there was no access to the Internet. Nonetheless it uncompressed the files. I then hooked up the printer to one of the two USB hubs. I then then tried to add a new printer. Unfortunately it seems that the system is not seiing that the printer is hooked up. Furthermore I can only install the driver for the DJ F300. I read on another thread that installing the DJ 3600 driver would work, but it is not part of the recognized and listed drivers neither in Ubuntu nor in the phlip.

So, I don't really know what's the real problem? How can I get Ubuntu to recognize the printer being hooked up to the USB hub and how can I make the printer work ?

Please help...

Thanks in advance.

FH

---

### Post by tribaal on 2006-12-07
I got mine working without any hacks with Edgy: just got to System -> Administration -> printer and add a new one. 

The driver I got it working with is the "Deskjet 3650" from hp (it's in the list of supplied drivers on edgy, no need to install it).

The scanner works even more easily: just run xsane :)

Hope this helps!

- trib'

---

### Post by MayItBe on 2006-12-07
Thanks. I'll try it.
FH

---

### Post by friedrich on 2006-12-07
same problem for me but xsane does not work. it cannot find any devices. printing works fine though on the 3650 driver.

---

### Post by tribaal on 2006-12-08
Hum sorry mate, for me scanning is as easy as turning on the peripheral and running XSane from the applications menu... There's a "searching for peripherals" dialog that comes in for a few seconds, then it just works.

Can't help you much more than that i'm afraid...

- trib'

---

### Post by friedrich on 2006-12-08
dammit. it just doesnt find mine..?

maybe i need an updated xsane or something? i searched synaptics but i had it all installed..

---

