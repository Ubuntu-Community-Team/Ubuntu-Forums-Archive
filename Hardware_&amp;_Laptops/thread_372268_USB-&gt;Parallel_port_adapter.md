---
title: "USB-&gt;Parallel port adapter"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by dabigjhall on 2007-02-28
I have a USB to parallel port adapter that I'm trying to use as a normal parallel port instead of a printer.  Is this possible?  lsusb lists the adapter as a "Prolific Technology, Inc. PL2305 Parallel Port".  I've tried to get it to work, but I'm still pretty new to Linux, particularly the hardware side of things.

I'd like to use this with my homemade AVR microcontroller programmer, which I used on the parallel port of my old computer.  I've looked around on the Internet for some other way to control it; if there is any way to get some basic digital I/O lines I can control on my computer, that would work, too.  I read about a USB interface board, but it was $45 and I'm trying to be, well, cheap :D

Oh, and I'm using Kubuntu 6.10

Any help is greatly appreciated!

---

### Post by johnc4510 on 2007-02-28
Here's a usb to parrallel port cable $19.99
[http://www.cablestogo.com/product.asp?cat%5Fid=1501&sku=16898&cm_mmc_o=-p8ByplCjCiIC4-q7GW-1CjCiNx%3dAl_%205ybEfwy%20gz_kwCjCAl_%205ybEfwy%20gz_kw&gclid=CI7Q5tSp0IoCFQLhYAodn14yQg](http://www.cablestogo.com/product.asp?cat%5Fid=1501&sku=16898&cm_mmc_o=-p8ByplCjCiIC4-q7GW-1CjCiNx%3dAl_%205ybEfwy%20gz_kwCjCAl_%205ybEfwy%20gz_kw&gclid=CI7Q5tSp0IoCFQLhYAodn14yQg)

Don't know if that will work the other way or not.

---

### Post by dabigjhall on 2007-02-28
Looks pretty similar to the one I have, but I guess there's no way to tell if it's the same chipset or not.

I'm not sure if I have the right driver loaded or configured correctly or whatnot.  I have the ppdev and parport modules loaded, and I did "sudo mknod /dev/usb/lp0 c 180 0" (one of the sites I found said to do that to make the device node thingy - something I'm still not very familiar with), but I can't get any I/O to work.  I wrote a small demo program just to test the I/O, and I'm pretty sure it's correct, but it could be the problem.  I can post the code if it would help.

Thanks for the help!

---

### Post by rickyrockrat on 2007-12-31
So did anybody ever find an adapter that works?  I've been looking for some time.  I've bought a USB245 debug module to see if I can use that, but it's gonna be a cludge.

---

