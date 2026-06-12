---
title: "netbooks and serial mice"
date: 2011-11-09
forum: Hardware
---

### Post by linuxhippy on 2011-11-09
I have a System 76 netbook that has 3 usb ports and no serial ports.  I also have an old Logitech Trackman serial marble mouse (3 button).  I put an adaptor on the mouse to make the serial end into a usb plug so that it fits into my netbook.  Now, how do I get it going?  I figure I need to edit xorg.conf but how?

I am running Ubuntu 10.04 on my netbook.

---

### Post by papibe on 2011-11-09
Hi linuxhippy.

I had a similar problem some time ago. I went to Microcenter to buy an adapter and was to pricey for me. I just bought a new mouse.

Just a thought,
Regards.

---

### Post by linuxhippy on 2011-11-12
Well, I got the mouse functioning on a pc with a serial adaptor but then messed up my netbook trying to make it work through a usb adaptor.  
Here's how to get the mouse going.  It's a 3 button logitech trackman marble mouse:

sudo inputattach --sunmouse /dev/ttyS0

However, when I tried this line using /dev/ttyUSB0 on my netbook I lost my wireless.  I figured out after this that my system76 star1 netbook wireless card is seen as a usb device...maybe inputattach pushed the wireless usb aside for the mouse which was on a usb adaptor.  A reboot and re-install of Ubuntu didn't make the wireless work.

I finally got help from a smart guy (he had this guide on how to upgrade your wireless card in your netbook: [http://www.vrekk.us/2010/08/taking-apart-system-76-star1.html](http://www.vrekk.us/2010/08/taking-apart-system-76-star1.html) ) who when I told him what I did told me to power down my netbook and remove the battery and power for a couple minutes and then push the power button to discharge any power that's left.  Then I powered back up and my wireless was back.  He said the mobo reset itself according to the driver modules that it found in Ubuntu.

So, I am just gonna put this serial mouse on an old desktop with a serial port and buy a usb marble mouse for the netbook.

---

