---
title: "Samsung U600 USB detection problems"
date: 2008-08-18
forum: Hardware
---

### Post by Adaemon on 2008-08-18
I'm using Ubuntu Studio Intrepid (alpha) and I have a Samsung U600 mobile phone with a serial to USB connector.  I have selected MASS STORAGE DEVICE mode on the phone but Ubuntu just refuses to detect its presence.  I feel I should make the point that twice out of the 15-20 times I've tried to connect the phone, it HAS been detected.  But I don't think I did anything different those times.  Mostly my lsusb output is:


Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Ie: nothing...

What can I do to resolve this issue?  I have found a couple of threads relating to USB devices not responding yet they either dry up before coming to a solution or I've tried their suggestions and they didn't work - ie. Installing Bitpim and configuring Hotplugging etc.  none of these have worked!

---

### Post by itix on 2008-08-19
Are you sure this isn't a problem with ubuntu being an alpha?
I have a Sony Ericsson w200i which connects like heaven to my computer when I put it in the equivalence of your "mass storage mode" (i.e. transfer mode).

Do you have a computer with a stable version of ubuntu or some other way to test if this works with a stable version?

---

### Post by jimmysheldon on 2008-08-28
i've got a samsung u600 and i'm running hardy, and im habing pretty much the same problem you are: i plug it in and bugger all happends. i also can't install samsung media studio :|

---

### Post by n00b@linux on 2008-08-29
Can you use bluetooth to get what you want done?

---

### Post by Zimmer on 2008-08-29
I think you will find that if you have not got an additional memory card in the phone it will not do a thing! The mass storage device mode detects the additional memory, not the internal phone memory. (I have a U600 and a G600. to view the internal phone folders I have to use Bluetooth, or copy files to the memory card and connect USB).

---

### Post by Zimmer on 2008-08-29
And if you you look quick enough on your phone display it flashes (and I mean 'flashes' ) a message to the effect of no memory card detected, please insert card...

memory is cheap ,I usually get mine from 7dayshop.com or cclonline.com

---

### Post by n00b@linux on 2008-08-29
Thx.  Does any MicroSD card work on the U600, eg. a generic 8GB MicroSD card?

---

### Post by Zimmer on 2008-08-29
largest it supports is 2 gig according to the review here...
[http://www.mobile-phones-uk.org.uk/samsung-u600.htm](http://www.mobile-phones-uk.org.uk/samsung-u600.htm)

I have 1gig in the G600 and have only filled half with music, pics and various apps I have for passing to other computer users.. Audacity, AVG etc.

---

### Post by jimmysheldon on 2008-08-30
nope can't use bluetooth, and don't have a memory card. so i'm pretty much stuffed then. hmm, guess i'll just have to keep trying and fiddling.

---

### Post by Zimmer on 2008-08-30
@jimmysheldon...
> nope can't use bluetooth, and don't have a memory card. so i'm pretty much stuffed then. hmm, guess i'll just have to keep trying and fiddling.

cough up a fiver for some memory ... free next day shipping! 

[http://www.cclonline.com/product-categories.asp?category_id=550](http://www.cclonline.com/product-categories.asp?category_id=550)

---

### Post by Hasen_A on 2008-09-18
Hello I have the same Problem with the new U900. Bluetooth works fine, but I would like to connect to it using the USB cable. Have you guys figured out yet how to do that?

I can connect to the phone using wammu. The device is '/dev/ttyACM0'. But the program does not let me transfer anything :(.

Cheers, Andreas

---

### Post by Zimmer on 2008-09-18
Yes. only IF you have an additional memory card inserted (microSD  see post #5 ) then you can go to your phone settings, find the USB settings options and select the one that says MASS STORAGE

Now if you attach the phone with a USB cable to your PC (Linux or Win) the PC will treat the installed card like a USB memory stick and mount it.

---

### Post by fuhrysteve on 2008-09-21
if you're trying to get bitpim to work, hotplug isn't used in the new linux 2.6 kernel.. instead it uses udev...

have you tried the instructions on this page for udev?
[http://www.bitpim.org/help/howto-linuxusb.htm](http://www.bitpim.org/help/howto-linuxusb.htm)

to get usb permissions to work right, you have to create a file:
```
sudo touch /etc/udev/rules.d/60-cell.rules
```

then, for a SAMSUNG phone (for different phones, check [here]("http://www.bitpim.org/help/ref-usbids.htm") and remove 0x from the beginning of the ID), add the following to that file:

```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"
# LG Phone
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="6601", MODE="0666"
LABEL="cell_rules_end"
```

works great for me (with the LG ID codes)

---

