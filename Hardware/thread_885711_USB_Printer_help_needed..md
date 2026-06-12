---
title: "USB Printer help needed."
date: 2008-08-10
forum: Hardware
---

### Post by Slug71 on 2008-08-10
Hey guys, im trying to install a USB HP C5180 printer. Ubuntu didnt detect it during install and im having a nightmare of a time getting it to work under Vista too. So i just figured ill spend more time getting it to work with Ubuntu and hopefully ditch Vista.
How would i find the Device URI for the Printer? Or check to see if it is recognised in a USB port?

---

### Post by Slug71 on 2008-08-10
Im using an Acer Extensa laptop, and was using Hardy but then decided to to install Intrepid Ibex to see if it would be detected by that. So still have Intrepid installed.

---

### Post by Slug71 on 2008-08-10
Bump...

---

### Post by coffeecat on 2008-08-10
> **Slug71 said:**
> im trying to install a USB HP C5180 printer. Ubuntu didnt detect it during install

I'm not quite sure what you mean by "didn't detect it during install". Do you mean when you were installing Ubuntu? You don't have to have a USB printer attached when you install Ubuntu. Once Ubuntu is set up, simply swicth the printer on (plugged into a USB port, of course) and go to System > Adminstration > Printing, and click on 'New Printer'. It should be autodetected and setting up is a breeze. It certainly always has been for both my HP and Samsung printers.

If a printer is supported in Linux, setting it up is easier than in Windows. If not, virtually impossible. However, [this Linux Foundation page]("http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C5180") shows that your printer is fully supported. Just make sure that the hplip and hpjis packages are installed - which they should be already.

Installing Intrepid may or may not have been a good idea. Intrepid won't handle a fully supported printer like yours any better than Hardy, and it's still in heavy development - read, still very buggy.

---

### Post by coffeecat on 2008-08-10
> **Slug71 said:**
> How would i find the Device URI for the Printer? Or check to see if it is recognised in a USB port?

I'm posting again because I was intrigued that a supported HP printer wasn't being autodetected. I'm posting from Ubuntu Hardy on my laptop in which, until now, I hadn't configured a printer. I've just plugged my HP Officejet 6310 (which, like yours, is a multifunction network and USB machine) into a USB port, switched it on and I didn't even have to go into System > Adminstration > Printing as I suggested before. A message balloon came down from the upper panel, saying 'Printer added 'Officejet_6300_series' is ready for printing', together with a 'Configure' button. It was as simple as that. Yours should do the same.

And, as far as network printing is concerned, it should be almost as easy. When I set the printer up in Ubuntu Hardy on my desktop machine and with the Officejet connected to my network via ethernet, I simply opened System > Administration > Printing, and there it was ready for a test page, with the URI already detected and filled in. One 'but' though. With the printer being given its IP address through DHCP by my router, the address was different the next time and I would have had to reconfigure. To avoid this, I found the IP address my router had assigned it, typed that in the address bar of firefox and found myself in the web configuration utility for the HP device, where I was able to set it up with a static address. Which was a pleasant surprise because there was nothing about web configuration in the documentation that came with the machine.

---

### Post by starcannon on 2008-08-10
I use an HP C4385 wireless printer, all I had to do what install the hplip packages from the Synaptic Package Manager, then run the Printer wizard, choose my printer out of the list of HP printers, everything on this printer works, the scanner, wifi network printing, card reader, ink level indicators, everything.

So far I've had nothing but excellent results from HP printers, never had to use the cups web admin tool yet, but as long as you have a working setup, and like the admin tools your using, then your set.

---

### Post by Slug71 on 2008-08-10
Thanks for the replies guys, it seems the problem is with the Printer. I think the USB port on the Printer is dead. I tried a different USB cable and also plugged it into my roomates Dell laptop loaded with XP and it doesnt even make a sound when i plug in the USB cable. Had it running fine on our old Laptop with XP before too. The printer powers on and everything though.

The beauty of Lightning i say!! Thats a T.V, Laptop, Wii, a couple AC Power Adaptors, Wireless Router and now the Printer from when lightning struck our house in June.

---

